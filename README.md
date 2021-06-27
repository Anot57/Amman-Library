# Amman-Library
The project (Amman Library) is a webpage where you can store details of different books. 
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/css/bootstrap.min.css" rel="stylesheet"
        integrity="sha384-+0n0xVW2eSR5OomGNYDnhzAbDsOXxcvSN1TPprVMTNDbiYZCxYbOOl7+AMvyTG2x" crossorigin="anonymous">

    <title>Project-2</title>
</head>
<body>
    <nav class="navbar navbar-expand-lg navbar-dark" style="background-color: #cde5f8;">
        <div class="container-fluid">
            <a class="navbar-brand" href="#" style="color: orangered;">Amman Library</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false"
                aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="#" style="color: rgb(207, 47, 7);">Home</a>
                    </li>
                </ul>
                <form class="d-flex">
                    <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
                    <button class="btn btn-outline-success" type="submit" style="color: rgb(65, 10, 194);">Search</button>
                </form>
            </div>
        </div>
    </nav>
    <!-- Alert tab -->
    <div class="message" id="message">
    </div>

    <div class="container">
        <br><br>
        <h1>Amman Library</h1>
        <hr>
        <form id="libraryForm">
            <div class="row mb-3">
                <label for="bookName" class="col-sm-2 col-form-label">Name:</label>
                <div class="col-sm-10">
                    <input type="text" class="form-control" id="bookName" placeholder="Book Name">
                </div>
            </div>
            <div class="row mb-3">
                <label for="Author" class="col-sm-2 col-form-label">Author</label>
                <div class="col-sm-10">
                    <input type="text" class="form-control" id="Author" placeholder="Author">
                </div>
            </div>
            <fieldset class="row mb-3">
                <legend class="col-form-label col-sm-2 pt-0">Type</legend>
                <div class="col-sm-10">
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="type" id="Fiction" value="Fiction" checked>
                        <label class="form-check-label" for="gridRadios1">
                            Fiction
                        </label>
                    </div>
                    <div class="form-check">
                        <input class="form-check-input" type="radio" name="type" id="Horror" value="Horror">
                        <label class="form-check-label" for="gridRadios2">
                            Horror
                        </label>
                    </div>
                    <div class="form-check disabled">
                        <input class="form-check-input" type="radio" name="type" id="Mystery" value="Mystery">
                        <label class="form-check-label" for="gridRadios3">
                            Mystery
                        </label>
                    </div>
                </div>
            </fieldset>
            <button type="submit" class="btn btn-primary" id="">Add Book</button>
        </form>
        <br><br>
        <h1>Your Books</h1>
        <table class="table table-striped table-hover table table-success table-striped" id="table">
            <thead>
                <tr>
                    <th scope="col">Name</th>
                    <th scope="col">Author</th>
                    <th scope="col">Type</th>
                </tr>
            </thead>
            <tbody id="tableBody"></tbody>
        </table>
    </div>

    <!-- <script src="JS-25.js"></script> -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-gtEjrD/SeCtmISkJkNUaaKMoLD0//ElJ19smozuHV6z3Iehds+3Ulb9Bn9Plx0x4"
        crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.2/dist/umd/popper.min.js"
        integrity="sha384-IQsoLXl5PILFhosVNubq5LC7Qb9DXgDA9i+tQ8Zj3iwWAwPtgFTxbJ8NT4GN1R8p"
        crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.1/dist/js/bootstrap.min.js"
        integrity="sha384-Atwg2Pkwv9vp0ygtn1JAojH0nYbwNJLPhwyoVbhoPwBhjQPR5VtM2+xf0Uwh9KtT"
        crossorigin="anonymous"></script>

</body>
<script>
    
    // Contructor.......
    function Book(name, author, type) {
        this.BookName = name;
        this.Author = author;
        this.Type = type;
    }

    // Display Constructor......
    function Display(params) {
        
    } 

    //Add methods to display prototypes.....
    Display.prototype.add = function(book) {
        console.log("Adding to UI");
        tableBody = document.getElementById("tableBody");
        let uiString = `<tr>
                    <td>${book.BookName}</td>
                    <td>${book.Author}</td>
                    <td>${book.Type}</td>
                </tr>`; 
        tableBody.innerHTML += uiString;         
    }

    //Implementing the clear function
    Display.prototype.clear = function() {
        let libraryForm = document.getElementById("libraryForm");
        libraryForm.reset
    }

    //Implementing the validate function
    Display.prototype.validate = function(book) {
        if(book.BookName.length < 2 || book.Author.length < 2){
            return false
        }   
        else{
            return true;
        }
    }

    // Implementing the show function.....
    Display.prototype.show = function(type, displayMessage){
        let message = document.getElementById("message");
        message.innerHTML = `<div class="alert alert-${type} alert-dismissible fade show" role="alert">
        <strong>Message: </strong> ${displayMessage}
        <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
        </div>`;
        setTimeout(function() {
            message.innerHTML = '';
        }, 2000);       //Here '2000' means 2000 millseconds = 2 secs...
    }

    // Add submit eventlistener to libraryForm....
    let libraryForm = document.getElementById("libraryForm");
    libraryForm.addEventListener("submit", libraryFormSubmit);
    function libraryFormSubmit(e) {
    
    let name = document.getElementById("bookName").value;
    let author = document.getElementById("Author").value;
   
    let type;
    let fiction = document.getElementById("Fiction");
    let horror = document.getElementById("Horror");
    let mystery = document.getElementById("Mystery");

    if(fiction.checked) {
        type = fiction.value;
    }
    else if (horror.checked) {
        type = horror.value;
    }
    else if (mystery.checked) {
        type = mystery.value;
    }

    let book = new Book(name, author, type);
    console.log(book);
    let display = new Display();
    if(display.validate(book)){
    display.add(book);      //This adds the book name,author and type in the table.. 
    display.clear();        //This clears the fields in the form.....
    display.show("success", " Your book is added successfully.");    
    }
    else{
        display.show("danger", ` Sorry, your book cannot be added.`);
    }     

    e.preventDefault();     //This method prevents dafault reloading of the page....
}

</script>
</html>
