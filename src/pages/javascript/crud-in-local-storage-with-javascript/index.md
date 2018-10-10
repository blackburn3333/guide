---
title: USE WEB STORAGE WITH JAVASCRIPT
---

<h2 align="center">USE WEB STORAGE WITH JAVASCRIPT</h2>
<p align="center">
  
  <img  width="200" src="https://i.imgur.com/Io7TaLm.png" title="jslogo" align="center"/>
</p>

<ul>
 <li>Store data in web storage</li>
 <li>Read data from web storage</li>
 <li>Delete data from web storage</li>
 <li>Update data from web storage</li>
</ul> 
<br/><br/>

<b>Store data in web storage</b>
<hr/>

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Web Storage</title>
</head>
<body>
    <input type="text" placeholder="Insert" id="data">
    <input type="submit" onclick="addToLocalStorage(document.getElementById('data').value)" value="Add">

    <div id="viewData">
    </div>

</body>

<script type="text/javascript">
    //read and store current web storage data
    storedData = JSON.parse(localStorage.getItem("storedData")) || [];

    //function for send data to web storage
    function addToLocalStorage(Data){
        storedData.push({Name:[Data]});//push data into array
        localStorage.setItem("storedData",JSON.stringify(storedData));//add array data into web storage
    }
</script>
</html>

```
<p>Make simple code template as above.

In the JavaScript first get current data form local storage and stored into storedData array variable. addToLocalStorage function read data from input and push into storedData after that send storedData data into local storage. This set and get functions of local storage use JSON for read and store.

You can see stored data using browser -> Right Click -> Inspect -> Select Application tab -> Select local storage form Storage Section (Google Chrome). following are the example
</p>
<p align="center">
  <img  src="https://i.imgur.com/ZooTSXz.png" title="jslogo" align="center"/>
</p>
<br/><br/>
<b>Read data from web storage</b>
<hr/>

```HTML
<script type="text/javascript">
    var ReadData = [];
    //Get items from local storage
    ReadData = JSON.parse(localStorage.getItem("storedData"));
  //read data from array
  for (var i = 0; i < ReadData.length; i++)
    {
    console.log(ReadData[i].Name);
    }
</script>
```

Above JavaScript code shows how to read data from local storage. First make and assign data to ReadData array variable from local storage. Read and data by using for loop. Following are the console output of local storage data.
<p align="center">
  <img src="https://i.imgur.com/oFDjpSy.png" />
</p>

<br/><br/>

<b>Delete data from web storage</b>
<hr/>

```HTML
<input type="button" onclick="DeleteData(3)" value="Delete data of 3rd index">
<script type="text/javascript">
//store current store data
storedData = JSON.parse(localStorage.getItem("storedData")) || [];


var ReadData = [];
ReadData = JSON.parse(localStorage.getItem("storedData"));

console.log("----------------------------");
console.log("|       BEFORE DELETE      |");
console.log("----------------------------");
for (var i = 0; i < ReadData.length; i++)
{console.log(ReadData[i].Name);}

function DeleteData(toDoID){
    //splice elemet from array by using array index
    storedData.splice(toDoID,1);
    //set spliced array into local storage
    localStorage.setItem("storedData", JSON.stringify(storedData));

    //assign and read new data afater splice
    ReadData = JSON.parse(localStorage.getItem("storedData"));
    console.log("----------------------------");
    console.log("|       After DELETE      |");
    console.log("----------------------------");
    for (var i = 0; i < ReadData.length; i++)
    {console.log(ReadData[i].Name);}
}

</script>
```
According to above code DeleteData function called for delete array element according to array index id following is the console output of before and after delete data from local storage.

<img src="https://i.imgur.com/KnHukGZ.png" />

<br/><br/>

<b>Update data from web storage</b>
<hr/>

```HTML
<input type="button" onclick="dataUpdate(3,'test Update Successful')" value="Update 3rd index">
<script type="text/javascript">
//store current store data
storedData = JSON.parse(localStorage.getItem("storedData")) || [];

var ReadData = [];
ReadData = JSON.parse(localStorage.getItem("storedData"));

console.log("----------------------------");
console.log("|       BEFORE Update      |");
console.log("----------------------------");
for (var i = 0; i < ReadData.length; i++)
{console.log(ReadData[i].Name);}

function dataUpdate(toDoID,updateValue){
    //remove old data and replace new data according to id
    ReadData.splice(toDoID, 1, { Name: [updateValue]});
    // set new items to local storage
    localStorage.setItem("storedData", JSON.stringify(ReadData));
    //readt and output new stored data form local storage
    ReadData = JSON.parse(localStorage.getItem("storedData"));
    console.log("----------------------------");
    console.log("|       AFTER Update      |");
    console.log("----------------------------");
    for (var i = 0; i < ReadData.length; i++)
    {console.log(ReadData[i].Name);}
}

</script>
```

In the dataUpdate function it remove old and replace new data according to array index id. Following are the console output of before and after update data.

<img src="https://i.imgur.com/jkjZRJX.png" />

<hr>

<h3 align="center">
EXAMPLE WEB APPLICTION FOR LOCAL STORAGES
</h3>
Simple application for make todo list. In this application can get idea about store, view, change and delete from HTML5 Web Storage using JavaScript and arrays.

GIT Repository
<a href="https://github.com/blackburn3333/MyToDo">https://github.com/blackburn3333/MyToDo</a>
DEMO
<a href="https://blackburn3333.github.io/MyToDo/">https://blackburn3333.github.io/MyToDo/</a>
<hr>
