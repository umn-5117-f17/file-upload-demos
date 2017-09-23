# Notes on file upload:

## server side (app.js)

Add multer to support "multipart" form submission.  (why? <https://stackoverflow.com/a/4526286/293087>)

https://expressjs.com/en/resources/middleware/multer.html

    npm install --save multer

See app.js.  Need to require and configure multer (to upload to memory).
There are many more options both on the client side and the server side
to control the limits and capabilities of the file upload process.

## client side (local.js)

There is a lot of old information on the web. It's pretty easy to upload
files these days.  This is one good post: <https://stackoverflow.com/a/8244082/293087>

The html form won't work right for file uploads without setting `enctype`:

    <form action="/upload-file-form" enctype="multipart/form-data" method="post">

<https://www.w3schools.com/TagS/att_form_enctype.asp>

jquery can access the file object:

    var f = $('#theinputfield')[0].files[0];

To create the appropriate object to send to the server:

    var fd = new FormData();
    fd.append('ajaxfile', f);

Then this string ('ajaxfile') must match up with the string we configure in
our node handler code.
