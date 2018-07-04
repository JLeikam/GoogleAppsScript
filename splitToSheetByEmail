// onFormSubmit
// gets submitted data
// checks if username has sheet
// if not makes sheet
// copy submitted data to user's sheet
function onFormSubmit(){
  
  // get the spreadsheet object
  var activeSpreadsheet = SpreadsheetApp.getActiveSpreadsheet();
  
  
  // within a google spreadsheet, we can get a sheet by name or by index  
  // for more info see:  https://stackoverflow.com/questions/20513002/how-to-get-sheet-that-is-not-first-sheet
  // var individualSheet = activeSpreadsheet.getSheetByName("Form Responses 1"); or...
  var indexOfFirstSheet = 0
  var individualSheet = activeSpreadsheet.getSheets()[indexOfFirstSheet];
  
  
  // get headings so we can transfer them to the sheet of the new student
  var row = 1;
  var column = 1;
  var numRows = 1;
  var numColumns = individualSheet.getLastColumn();
  var headings = individualSheet.getRange(row, column, numRows, numColumns).getValues();
  
  // get response of student to transfer to new spreadsheet
  row = individualSheet.getLastRow();
  column = 1;
  numRows = 1;
  numColumns = individualSheet.getLastColumn();
  var lastRow = individualSheet.getRange(row, column, numRows, numColumns).getValues();
  
  
  
  // get student email
  row = 0;
  column = 1;
  var studentEmail = lastRow[row][column];
  
  
  // check if student already has their own sheet
  if(activeSpreadsheet.getSheetByName(studentEmail)){
    var studentSheet = activeSpreadsheet.getSheetByName(studentEmail);
  }
  // else make a new one
  else{
    var sheetName = studentEmail;
    var studentSheet = activeSpreadsheet.insertSheet(sheetName);
   
    //transfer headings
    row = 1;
    column = 1;
    numRows = 1;
    numColumns = headings[0].length;
    studentSheet.getRange(row, column, numRows, numColumns).setValues(headings);
    
    
  }
  
  //copy submitted data to student sheet
  row = studentSheet.getLastRow() + 1; // + 1 so we don't overwrite data of previous row
  column = 1;
  numRows = 1;
  numColumns = lastRow[0].length;
  studentSheet.getRange(row, column, numRows, numColumns).setValues(lastRow);
  
  
}





