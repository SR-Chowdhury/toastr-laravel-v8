# toastr.js
## ToastrJS is a JavaScript library for Gnome / Growl type non-blocking notifications. jQuery is required. The goal is to create a simple core library that can be customized and extended.

# Setup Guide
> **N.B.** Try to update CDN Link
> [toastrn latest `toastr.min.css` & `toastr.min.js`](https://cdnjs.com/libraries/toastr.js/latest)

**welcome.blade.php**
```
  <!doctype html>
  <html lang="en">
    <head>
      <!-- Required meta tags -->
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <meta name="author" content="Shihanur Rahman Chowdhury">

      <!-- Bootstrap CSS -->
      <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6" crossorigin="anonymous">
      
      <!-- toastr CSS (includes Bootstrap)-->
      <link href="{{ asset('public//assets/v1.0/toastr_styles.css')}}" rel="stylesheet" />
      
      <!-- Toastr CDN -->
      <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.css">

      <title>Explore SuperStar World</title>
      
    </head>
    <body>
      <h1>Bismillahir Rahmanir Rahim</h1>


      <!-- Bootstrap Bundle with Popper -->
      <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.bundle.min.js" integrity="sha384-JEW9xMcG8R+pH31jmWH6WWP0WintQrMb4s7ZOdauHnUtxwoG2vI5DkLtS3qm9Ekf" crossorigin="anonymous"></script>
      
      <!-- JQuery CDN-->
      <script src="https://code.jquery.com/jquery-3.6.0.min.js" integrity="sha256-/xUj+3OJU5yExlq6GSYGSHk7tPXikynS7ogEvDej/m4=" crossorigin="anonymous"></script>
            
      <!-- toastr CDN-->
      <script src="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/js/toastr.min.js"></script>
      
      <!-- toastr JS-->
      <script src="{{ asset('public/assets/v1.0/toastr_scripts.js') }}"></script>
    
      <script>
            @if (Session::has('message'))

                var type = "{{ Session::get('alert-type', 'success') }}"

                switch(type) {
                    case 'success' :
                        toastr.success(" {{ Session::get('message') }} ");
                        break;
                    case 'info' :
                        toastr.info(" {{ Session::get('message') }} ");
                        break;
                    case 'warning' :
                        toastr.warning(" {{ Session::get('message') }} ");
                        break;
                    case 'error' :
                        toastr.error(" {{ Session::get('message') }} ");
                }

            @endif
        </script>
    </body>
  </html>
```

**myController.php**
```
  if($something) {
      $notification = array(
          'message' => 'Alhamdulillah, Data is successfully inserted',
          'alert-type' => 'success'
      );
      return Redirect()->back()->with($notification);
  }
  else {
      $notification = array(
          'message' => 'Ops! something went wrong',
          'alert-type' => 'error'
      );
      return Redirect()->back()->with($notification);
  }
```
