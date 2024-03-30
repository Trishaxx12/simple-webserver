# EX01 Developing a Simple Webserver
## Date:30/03/2024

## AIM:
To develop a simple webserver to serve html pages.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
```
from http.server import HTTPServer, BaseHTTPRequestHandler

content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
    <style>
        body{
            background-image: url('caffee.jpg');
        }
        body{
            background-image: url('caffee.jpg');
            height: -25%;
            background-repeat: no-repeat;
            background-size: cover;
            align-items: center;
          
        }
        .section-heading{
            font-size: 7rem;
            font-weight: 600;
            color: whitesmoke;
            text-align: center;
            text-transform: capitalize;
            letter-spacing: 0.5rem;
            text-shadow: 0.3rem 0.3rem 0.3rem #000;
        }
        
        
        
        
        .navbar{
            position: fixed;
            top: -8rem;
            z-index: 5;
            width: 100%;
            height: 12rem;
            background-color: #000;
            display: flex;
            justify-content: center;
            align-items: center;
            box-shadow: 0.2rem 0.2rem 0.2rem #000;
            transition: top 0.5s;
        } 
        a{
            width: 55%;
            color: whitesmoke;
            margin-right:5px;
            position:relative;
            float:right;
            margin-left: 70px;
            font-style: italic;
        }
        .icon{
            color: white;
            font-size: 20px;
            padding: 5px;
            
        }
        i:hover{
            color: darkgrey;
        }
        .a{
            width: 55%;
            color: whitesmoke;
            margin-right:5px;
            position:relative;
            float:right;
            margin-left: 70px;
            font-style: italic;
        }
        .section-2{
            font-size: 1.5cm;
            color: beige;
            align-items: center;
            justify-content: center;
            font-size: 7rem;
            font-weight: 600;
            color: whitesmoke;
            text-align: center;
            text-transform: capitalize;
            letter-spacing: 0.5rem;
            text-shadow: 0.3rem 0.3rem 0.3rem #000;
        }
        img{
            padding-left: 450px;
            padding-right: 450px;
            padding-top: 50px;
            padding-bottom: 1050px;
        }
    </style>
    
</head>
<body>
    <div class="row border border-3 bgc">
        <div class="col-5 ">
            <i class="bi bi-twitter icon"></i>
            <i class="bi bi-youtube icon"></i>
            <i class="bi bi-whatsapp icon"></i>
            <i class="bi bi-linkedin icon"></i>
            <i class="bi bi-facebook icon"></i>
            <i class="bi bi-instagram icon"></i>


        </div>
        <div class="col-5" >
    <div style="display: flex;" >
        <a class="a"></a>
        <a href="">Home</a>
        <a href="">About</a>
        <a href="">HotDrinks</a>
        <a href="">SoftDrinks</a>
        <a href="">pizza</a>
        <a href="">cakes</a>
    </div></div>
    <section class="section-1">
        <h1 class="section-heading">
           THE TUSCAN TABLE
        </h1>
        <section class="section-2">
            <h2 class="h2">
                Meals We Love
            </h2>
            <div id="carouselExampleIndicators" class="carousel slide" data-bs-ride="carousel" data-bs-interval="1000">
                <div class="carousel-indicators">
                  <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
                  <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="1" aria-label="Slide 2"></button>
                  <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="2" aria-label="Slide 3"></button>
                  <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="3" aria-label="Slide 4"></button>
                  <button type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide-to="4" aria-label="Slide 5"></button>
                </div>
                
                <div class="carousel-inner">
                  <div class="carousel-item active">
                    <img src="A.jpg" class="d-block w-100" alt="..." width="5cm">
                  </div>
                  <div class="carousel-item">
                    <img src="B.jpg" class="d-block w-100" alt="...">
                  </div>
                  <div class="carousel-item">
                    <img src="C.jpg" class="d-block w-100" alt="...">
                  </div>
                  <div class="carousel-item">
                    <img src="D.jpg" class="d-block w-100" alt="...">
                  </div>
                  <div class="carousel-item">
                    <img src="E.jpg" class="d-block w-100" alt="...">
                  </div>
                </div>
                <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
                  <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                  <span class="visually-hidden">Previous</span>
                </button>
                <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
                  <span class="carousel-control-next-icon" aria-hidden="true"></span>
                  <span class="visually-hidden">Next</span>
                </button>
              </div>
                <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
</body>
</html>
"""
class MyHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        print("request received")
        self.send_response(200)
        self.send_header('Content-type', 'text/html; charset=utf-8')
        self.end_headers()
        self.wfile.write(content.encode())

server_address = ('', 8000)
httpd = HTTPServer(server_address, MyHandler)

print("my webserver is running...")
httpd.serve_forever()

```


## OUTPUT:
![simplewebserver](https://github.com/Trishaxx12/simple-webserver/assets/165448504/7625be0d-ae59-430a-aaaf-c3277f78ae77)



## RESULT:
The program for implementing simple webserver is executed successfully.
