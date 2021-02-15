So in this README file you will be shown how to set up PaginationJS in your own project. This file assumes you have a working knowledge of HTML and JavaScript. First things first you are going to want to include the paginationJS.js in your own project and link the script to the page you want to use it on. 

Once that is set up you will need a variable that contains a list of your data. Now, this can be a regular array of strings or integers or even as advanced as an array of objects. The library is built to account for almost all types of arrays. 
Example of a data array:

 var data = [
              {
                  Task_Id: "1",
                  Task_Name: "clean room",
              },
              {
                  Task_Id: "2",
                  Task_Name: "fix Computer",
              },
              {
                  Task_Id: "3",
                  Task_Name: "Finish homework",
              }
            ]

tableHeaders is a property that is required for the program to work. After you have created a variable with your data you will next want to create a variable for your headers. These are going to be the column headers displayed on each column of the table. It is important to note here, the position of the column headers and the position of the properties matter, However, they are ordered on your data, and the header array is how they will be displayed. So make sure your header lines up with your properties.
Example of a header array:
   var table = new Table(data, {
      tableHeaders: ["Id", "Name", "Start Time"]

    });

    Note: the table header will displayed with the "Id" being first in this example so remember to keep
    your field name inputs and the table headers in the same index.

tableId is the id of the element you wish to display the table in, this field is required in order for 
the program to work. 

var table = new Table(data, {
      tableHeaders: ["Id", "Name", "Start Time"],
      tableId: document.getElementById("mainTable"),
});


fields is the object fields that are inside the array of objects. This allows some items not to be displayed.
This field is required in order for the program to work. Here is an example

    var table = new Table(data, {
      tableHeaders: ["Id", "Name", "Start Time"],
      tableId: document.getElementById("mainTable"),
      fields: ["Id", "Name", "Start Time"],
      
    });

numOfItemsDropdownDisplay is a object property that is not required in order for the program to work. 
the object has 2 properties, the first is a boolean called "display", if set to true it will displayed
the dropdown. the second property is the numbers you want in the dropdown, these numbers have to be
full  numbers no negative or decimals allowed. Also a div with the id of "numOfItemsDisplay" must be in the html of the page

   <div id="numOfItemsDisplay"></div>

   <script>
    var table = new Table(data, {
      tableHeaders: tableHeads,
      tableId: sourceId,
      fields: objectFields,
      numOfItemsDropdownDisplay: {
        display: true,
        numberList: ["5","10","15"]
      }
    });
   </script>

searchBarDisplay is a boolean property that is not required in order for the program to work. if
the boolean is set to true then a search bar will be displayed. If nothing is inputed it will 
automatically be set to false; Also if set to true, this property will require a div with the Id 
named "searchBar". Here is an example

  <div id="searchBar"></div>

   <script>
      var table = new Table(data, {
      tableHeaders: tableHeads,
      tableId: sourceId,
      fields: objectFields,
      numOfItemsDropdownDisplay: true,
      searchBarDisplay: true,
    });
   </script>

specialButtons is a array of objects property that is not required for the program to work.
This property allows the user to put in special buttons at the end of their table, things like
edit or delete, or anything since this is pretty customizable. The objects for this program
have 3 properties. They are "btnName","btnClasses","text". Note in order for you to add events to these buttons
you will have to do that are your own as the library does not support that functionality inside of it


  <script>
      var table = new Table(data, {
      tableHeaders: tableHeads,
      tableId: sourceId,
      fields: objectFields,
      numOfItemsDropdownDisplay: true,
      searchBarDisplay: true,
      specialButtons: [
        {
          btnName: "edit",
          btnClasses: ["btn", "btn-warning"],
          text: "Edit"
        },
        {
          btnName: "delete",
          btnClasses: ["btn", "btn-danger"],
          text: "Delete"
        }
      ]
    });
  </script>
    


Updates for the future
-> Allow the header variable to read in an object, with one property being the header title, another being the data property it is tied to and finally a property for the placement of the column.    
-> Have the library handle event listeners on custom buttons
-> Add ability for the user to style the table on their own