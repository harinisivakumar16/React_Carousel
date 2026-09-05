# Ex05 Image Carousel
## Date:

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
ImageCarousel.jsx
```
import React, { useState } from "react";
import "./ImageCarousel.css";

function ImageCarousel() {
  const images = [
    "https://images.unsplash.com/photo-1506744038136-46273834b3fb?w=600&h=400&fit=crop",
    "https://images.unsplash.com/photo-1500534623283-312aade485b7?w=600&h=400&fit=crop",
    "https://images.unsplash.com/photo-1470770841072-f978cf4d019e?w=600&h=400&fit=crop",
    "https://images.unsplash.com/photo-1501785888041-af3ef285b470?w=600&h=400&fit=crop"
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  function nextImage() {
    setCurrentIndex((currentIndex + 1) % images.length);
  }

  function previousImage() {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  }

  return (
    <div className="carousel">
      <h1>Image Carousel</h1>

      <img
        src={images[currentIndex]}
        alt="Carousel"
        className="carousel-image"
      />

      <div className="buttons">
        <button onClick={previousImage}>
          ❮ Previous
        </button>

        <span>
          {currentIndex + 1} / {images.length}
        </span>

        <button onClick={nextImage}>
          Next ❯
        </button>
      </div>
    </div>
  );
}

export default ImageCarousel;
```
ImageCarousel.css
```
.carousel {
  width: 650px;
  margin: 50px auto;
  text-align: center;
  font-family: Arial, sans-serif;
}

.carousel h2 {
  margin-bottom: 20px;
}

.carousel-image {
  width: 600px;
  height: 400px;
  object-fit: cover;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.buttons {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 25px;
  margin-top: 20px;
}

.buttons button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.buttons button:hover {
  background-color: #ddd;
}

.buttons span {
  font-size: 16px;
  font-weight: bold;
}
```
App.jsx
```
import React from "react";
import ImageCarousel from "./ImageCarousel.jsx";

function App() {
  return (
    <div>
      <ImageCarousel />
    </div>
  );
}

export default App;
```
## OUTPUT
<img width="1915" height="967" alt="image" src="https://github.com/user-attachments/assets/9424713d-5a12-4164-ad2c-c058ea67fe36" />
<img width="1392" height="896" alt="image" src="https://github.com/user-attachments/assets/aa4664db-b5df-4112-a3f6-69b1e050468a" />
<img width="1392" height="901" alt="image" src="https://github.com/user-attachments/assets/28d5333d-68cf-4556-a5d8-f163a0211007" />
<img width="1403" height="902" alt="image" src="https://github.com/user-attachments/assets/d855e328-fe23-4d8a-a5d3-5bdbab7c2b04" />

## RESULT
The program for creating Image Carousel using React is executed successfully.
