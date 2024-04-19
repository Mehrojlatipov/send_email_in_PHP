# send_email_in_PHP


#    html uchun kod

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>

</head>

<body>
  <div class="container">
    <form id="contact" action="mail.php" method="post">
      <h1>Contact Form</h1>

      <fieldset>
        <input placeholder="Your name" name="name" type="text" tabindex="1" autofocus>
      </fieldset>
      <fieldset>
        <input placeholder="Your Email Address" name="email" type="email" tabindex="2">
      </fieldset>
      <fieldset>
        <input placeholder="Type your subject line" type="text" name="subject" tabindex="4">
      </fieldset>
      <fieldset>
        <textarea name="message" placeholder="Type your Message Details Here..." tabindex="5"></textarea>
      </fieldset>

      <fieldset>
        <button type="submit" name="send" id="contact-submit">Submit Now</button>
      </fieldset>
    </form>
  </div>
</body>

</html>




## php uchun kod


<?php
use PHPMailer\PHPMailer\PHPMailer;
use PHPMailer\PHPMailer\Exception;

require 'phpmailer/src/Exception.php';
require 'phpmailer/src/PHPMailer.php';
require 'phpmailer/src/SMTP.php';

if (isset($_POST["send"])) {

  $mail = new PHPMailer(true);


    $mail->isSMTP();                              
    $mail->Host       = 'smtp.gmail.com';       
    $mail->SMTPAuth   = true;             
    $mail->Username   = 'mehrojlatifov06@gmail.com';
    $mail->Password   = 'doorqyknyjihqbkv'; 
    $mail->SMTPSecure = 'ssl';
    $mail->Port       = 465;                                    

    $mail->setFrom( $_POST["email"], $_POST["name"]); 
    $mail->addAddress('mehrojlatifov06@gmail.com');    
    $mail->addReplyTo($_POST["email"], $_POST["name"]); 

    //Content
    $mail->isHTML(true);              
    $mail->Subject = $_POST["subject"];  
    $mail->Body    = $_POST["message"]; 

  
    $mail->send();
    echo
    " 
    <script> 
     alert('Message was sent successfully!');
     document.location.href = 'index.php';
    </script>
    ";
}
?>
