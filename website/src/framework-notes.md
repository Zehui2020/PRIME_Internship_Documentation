# Framework Notes
1. To export to excel, the pmtseafood portal uses a few third-party files installed through `composer`. However, due to the version being an older one, with multiple third-party files, it's very hard to accuratley install them through `composer`. Please ask your supervisor to download the `vendor` files on their side and install them manually.

1. We'll be looking at the `picking-list.php` as an example:
    ```html
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
    <button type="submit" id="export-fulfilled" name="export-fulfilled" onclick="exportFulfilled()" class="btn mr-1 rounded-0 btn-dark border">Export Fulfilled</button>
    ```
    1. Using the `onclick` tag, we can call a function when the button is clicked. The function is as follows:
        ```php
        function exportFulfilled() 
        {
            var uid = $('#user_id').find(":selected").val();
            var pid = $('#product_id').find(":selected").val();
            var url = "excel.php?action=picking-list-fulfilled&user_id="+uid+"&product_id="+pid+"&date-filter="+$("#datepicker").val();
            window.open(url, '_blank').focus();
        }
        ```
        1. We can hardcode a url that has the `action` tag to trigger a `$_POST` request of `picking-list-fulfilled`, along with other vairables like `uid`, `pid`, etc.
        1. This is to load the `excel.php` page using `window.open(url, '_blank').focus();` to open it in a new tab, thus calling the code inside `excel.php`.

    1. Inside `excel.php`, we'll look for the `picking-list-fulfilled` action and respond accordingly:
        1. Get all the required data using an SQL query. 
        1. Call the `findPO` function to get an `associative array` of `product orders` using the data we got from the SQL query.
        1. We then store the required data into `associative array` (e.g. customer usernames, product PLUs, UOMs, etc.)
        1. Then call the function `processPickingListFulfilledExcel` to generate the excel file.
        ```php
        else if($action == "picking-list-fulfilled") 
        {
            ...
            $orders = findPO($link, $filterUserID, $filterProductID, $dateFilter);
            ...
            processPickingListFulfilledExcel($data, $customerList, $dateFilter);
        }
        ```
    1. Inside the `processPickingListFulfilledExcel` function, we:
        1. Instantiate a new `Spreadsheet` object and get the active sheet.
            ```php
            function processPickingListFulfilledExcel($data, $customerList, $date) 
            {
                $spreadsheet = new Spreadsheet();
                $sheet = $spreadsheet->getActiveSheet();
                ...
            }
            ```
        1. We then define a few styles on how the data should be displayed in the excel sheet (e.g. font size, alignment, etc.).
            ```php
            function processPickingListFulfilledExcel($data, $customerList, $date) 
            {
                ...
                $boldCenterStyle = array(
                    'font' => [
                        'bold' => true,
                    ],
                    'alignment' => array(
                        'horizontal' => \PhpOffice\PhpSpreadsheet\Style\Alignment::HORIZONTAL_CENTER,
                    )
                );
                ...
            }
            ```
        1. To apply the style & setting the values in excel, we'll use excel's coordinate system (A1, E3, F6, etc.):
            ```php
            function processPickingListFulfilledExcel($data, $customerList, $date) 
            {
                ...
                $sheet->setCellValue('A3', 'No');
                $sheet->getStyle("A3")->applyFromArray($styleArray);
                ...
            }
            ```
            1. This will mean the value of cell `A3` in the excel sheet will say `No` and will take on the style of `$styleArray`.

        1. After all the values in the excel sheet is set, the `filename` is set and automatically downloaded using this:
            ```php
            $fileName = 'Picking_List_Fulfilled' . '_' . date("dmY", strtotime($date)).".xlsx";
            
            header('Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet');
            header('Content-Disposition: attachment;filename="'.$fileName.'"');
            header('Cache-Control: max-age=0');
            header('Cache-Control: max-age=1');
            header('Cache-Control: cache, must-revalidate');
            header('Pragma: public');

            $writer = IOFactory::createWriter($spreadsheet, 'Xlsx');
            $writer->save('php://output');
            ```