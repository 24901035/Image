# Ex.08 Design of Interactive Image Gallery

## AIM
  To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS

## Step 1:

Clone the github repository and create Django admin interface

## Step 2:

Change settings.py file to allow request from all hosts.

## Step 3:

Use CSS for positioning and styling.

## Step 4:

Write JavaScript program for implementing interactivit

## Step 5:

Validate the HTML and CSS code

## Step 6:

Publish the website in the given URL.

## PROGRAM
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <title>IMAGE GALLERY</title>
    <link rel="icon" href="LOGO.png">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            background-color: #d4efea;
            color: #333;
        }

        .container {
            max-width: 1000px;
            margin: 40px auto;
            background: lightcyan;
            padding: 20px 40px;
            border-radius: 12px;
            box-shadow: 0 6px 18px rgba(0,0,0,0.07);
        }
    
        .image-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
        }

        .image {
            background: #ecf0f1;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            overflow: hidden;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
        }

        .image:hover {
            transform: translateY(-8px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .image img {
            width: 100%;
            height: 350px;
            object-fit: cover;
            border-bottom: 3px solid #1abc9c;
        }
        #lightbox {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 900px;
            background: rgba(0,0,0,0.85);
            display: flex;
            justify-content: center;
            align-items: center;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s ease;
            z-index: 1000;
        }

        #lightbox.visible {
            opacity: 1;
            visibility: visible;
        }

        #lightbox img {
            max-width: 90%;
            max-height: 90%;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(255,255,255,0.4);
        }

        #lightbox span {
            position: absolute;
            color: white;
            font-size: 40px;
            font-weight: bold;
            cursor: pointer;
            user-select: none;
        }

        #close {
            top: 30px;
            right: 40px;
            font-size: 45px;
        }

        #prev {
            left: 40px;
            font-size: 60px;
        }

        #next {
            right: 40px;
            font-size: 60px;
        }
    </style>
</head>
<body>
    
    <div class="container">
        <div class="image-grid">
            <div class="image"><img src="asta.jpg" alt="Asta" /></div>
            <div class="image"><img src="baki.png" alt="Baki" /></div>
            <div class="image"><img src="goku.jpg" alt="Goku" /></div>
            
    </div>
    <div id="lightbox">
        <span id="close">&times;</span>
        <span id="prev">&#10094;</span>
        <img src="" alt="Preview">
        <span id="next">&#10095;</span>
    </div>

    <script>
        const images = document.querySelectorAll("img");
        const lightbox = document.getElementById("lightbox");
        const lightboxImg = lightbox.querySelector("img");
        const closeBtn = document.getElementById("close");
        const prevBtn = document.getElementById("prev");
        const nextBtn = document.getElementById("next");

        let currentIndex = 0;

        function showImage(index) {
            currentIndex = index;
            lightboxImg.src = images[index].src;
            lightbox.classList.add("visible");
        }

        images.forEach((img, index) => {
            img.addEventListener("click", () => showImage(index));
        });

        closeBtn.addEventListener("click", () => {
            lightbox.classList.remove("visible");
        });

        prevBtn.addEventListener("click", (e) => {
            e.stopPropagation();
            currentIndex = (currentIndex - 1 + images.length) % images.length;
            lightboxImg.src = images[currentIndex].src;
        });

        nextBtn.addEventListener("click", (e) => {
            e.stopPropagation();
            currentIndex = (currentIndex + 1) % images.length;
            lightboxImg.src = images[currentIndex].src;
        });
        lightbox.addEventListener("click", (e) => {
            if (e.target === lightbox) {
                lightbox.classList.remove("visible");
            }
        });
        document.addEventListener("keydown", (e) => {
            if (e.key === "Escape") {
                lightbox.classList.remove("visible");
            }
        });
    </script>
</body>
</html>

```


## OUTPUT
![alt text](<Screenshot 2025-11-16 165154.png>)

## RESULT
  The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
