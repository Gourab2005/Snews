<h1>Fixing bugs</h1>
bug1. center all items from top-bottom in header part
//top: 50%;
transform: translate(-0%,-50%);//
--> attach this property to the parant div

<!-- setting up html and js in appscript -->
<!-- html -->
<!-->
<!DOCTYPE html>
<html>

<head>
  <base target="_top">
  <script>
    function AddRow() {
      var usernamee = document.getElementById("Createusername").value;
      var passwordd = document.getElementById("Createpassword").value;
      var email = document.getElementById("email").value;
      var phone = document.getElementById("phone").value;
      if (usernamee == "" || passwordd == "" || email == "" || phone == "") {
        return false;
      } else {
        google.script.run.AddRecord(usernamee, passwordd, email, phone);
        document.getElementById("page2_id1").className = "page2_class1";
      }
    }

    function Loginuser() {
      var username = document.getElementById("username").value;
      var password = document.getElementById("password").value;
      google.script.run.withSuccessHandler(function (output) {
        if (output == 'TRUE') {
          var url1 = 'https://sourcify.000webhostapp.com/';
          var winRef = window.open(url1);
          winRef ? google.script.host.close() : window.onload = function () {
            document.getElementById('url').href = url1;
          };
        } else if (output == 'FALSE') {
          document.getElementById("errorMessage").innerHTML = "Username or Password Not Correct";
        }
      }).checkLogin(username, password);
    }

    function function1() {
      document.getElementById("page1_id1").className = "page1_class1-off";
      document.getElementById("page2_id1").className = "page2_class1";
    }

    function function3() {
      document.getElementById("page3_id1").className = "page3_id1-off";
      document.getElementById("page1_id1").className = "page1_class1";
    }
  </script>
  <style>
    /* page1 */
    .page1_class1-off {
      display: none;
    }

    /* page2 */
    .page2_class1 {
      display: none;
    }

    .page2_id1-off {
      display: none;
    }

    /* page3 */
    .page3_class1 {
      display: none;
    }

    .page3_id1-off {
      display: none;
    }

    input[type=text]:hover {
      border-bottom: 2px solid black;
    }

    input[type=number]:hover {
      border-bottom: 2px solid black;
    }

    input[type=password]:hover {
      border-bottom: 2px solid black;
    }
  </style>

  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>

<body>
  <br><br>
  <!-- page1 ->
  <center>
    <div class="page1_class1" id="page_id1" style="background:none;border:2px solid gray;border-radius: 20px;width: 250px;padding-top: 18px;padding-bottom: 20px;padding-left: 20px;padding-right: 20px;">
      <h1>Login</h1>
      <br>
      <input type="text" id="username" placeholder="Username" style="border-top: none;border-right: none;border-left: none; outline: none; text-align: center; font-size:0.9em; width: 50%; font-weight:bold;">
      <br>

      <input type="password" id="password" placeholder="Password" style="border-top: none;border-right: none; border-left: none; outline: none; text-align: center; font-size:0.9em; width: 50%; font-weight:bold;"/>
      <br><span id="errorMessage" style="color:red"></span><br>

      <input type="submit" value="Login" onclick="Loginuser()" style="float: right;padding-top: 1px;padding-bottom: 1px;padding-left: 10px;padding-right: 10px; font-size: 0.9em; font-weight:bold;"/><br>
      <br>
      <b>If you don't have an account,then signup first</b>
      <!-- <input type="button" onclick="function1()" value="Create New" style="margin-top: 5px;font-weight:bold;"/>
    </div> -->

<!-->
    <div class="page2_class1" id="page2_id1" style="background:none;border:2px solid gray;border-radius: 20px;width: 250px;padding-top: 10px;padding-bottom: 20px;padding-left: 20px;padding-right: 20px;">
      <h1> Create Account</h1>
      <br>
      <input type="text" id="Createusername" placeholder="Name" style="border-top: none;border-right: none;border-left: none; outline: none; text-align: center; font-size:0.9em; width: 50%; font-weight:bold;">
      <br>
      <input type="password" id="Createpassword" placeholder="Create password" style="border-top: none;border-right: none; border-left: none; outline: none; text-align: center; font-size:0.9em; width: 50%; font-weight:bold;"/>
      <br>
      <input type="text" id="email" placeholder="Email" style="border-top: none;border-right: none; border-left: none; outline: none; text-align: center; font-size:0.9em; width: 50%; font-weight:bold;"/>
      <br>
      <input type="number" id="phone" placeholder="Phone no." style="border-top: none;border-right: none; border-left: none; outline: none; text-align: center; font-size:0.9em; width: 50%; font-weight:bold;"/>
      <br>
      <br>
      <b style="color:red;">Password must contain letters and numbers. It will not work without letters and numbers.</b>
      <br><br>
      <input type="submit" value="Create" onclick="AddRow()" style="float:right; padding-top: 1px; padding-bottom:1px; padding-left:10px;padding-right:10px; font-size:0.9em; font-weight:bold;"/>
      <br>
    </div>

<!-- >
    <div class="page3_class1" id="page3_id1" style="background:none;border:2px solid gray;border-radius: 20px;width: 250px;padding-top: 10px;padding-bottom: 20px;padding-left: 20px;padding-right: 20px;">
      <h2>Your account has been successfully created. Login to your account</h2>
      <input type="submit" onclick="function3()" value="Login" style="font-weight:bold;"><br>
    </div>
  </center>
</body>

</html>

*/

<!-- js -->

<!-- ->
function doGet(e) {
  var template = HtmlService.createTemplateFromFile("index");
  template.xFrameOptionsMode = HtmlService.XFrameOptionsMode.ALLOWALL;
  return template.evaluate();
}

function checkLogin(username, password) {
  var url = 'https://docs.google.com/spreadsheets/d/1K_FIzwlt3xKDaiyGuueRwPIrmP7Z3PtUsVm-cd7JOg0/edit#gid=957106728';
  var ss = SpreadsheetApp.openByUrl(url);
  var webAppSheet = ss.getSheetByName("Form Responses 1");
  var dataRange = webAppSheet.getDataRange();
  var values = dataRange.getValues();

  var found_record = false;

  for (var i = 0; i < values.length; i++) {
    var storedUsername = values[i][1].toUpperCase();
    var storedPassword = values[i][2].toUpperCase();

    if (storedUsername == username.toUpperCase() && storedPassword == password.toUpperCase()) {
      found_record = true;
      break;
    }
  }

  return found_record ? 'TRUE' : 'FALSE';
}

function AddRecord(username, password, email, phone) {
  var url = 'https://docs.google.com/spreadsheets/d/1K_FIzwlt3xKDaiyGuueRwPIrmP7Z3PtUsVm-cd7JOg0/edit#gid=957106728';
  var ss = SpreadsheetApp.openByUrl(url);
  var webAppSheet = ss.getSheetByName("Form Responses 1");
  webAppSheet.appendRow([username, password, email, phone]);
}


<!-- opening a link in the same tab without changing to new Tab -->
use target="_self" inside a tag

<!-- using font awsome logo and fonts -->
Font awsome dn attachment this link ccopied from https://cdnjs.com/libraries/font-awesome 
 and
for icon code https://fontawesome.com/search-->

