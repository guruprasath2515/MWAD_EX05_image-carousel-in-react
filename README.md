# MWAD_EX05_image-carousel-in-react
## Name:GURU PRASATH R
## Reg.no:212223040053

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
## app.jsx
```
import React from 'react';
import ImageCarousel from './ImageCarousel';

import currency  from './assets/img1.jpeg';
import exchange from './assets/img2.jpeg';
import trading from './assets/img3.jpeg';
import buy_sell from './assets/img4.jpeg';
import go_up from './assets/img5.jpeg';


const App = () => {
  const images = [currency,exchange,trading,buy_sell,go_up];

  return (
    <div>
      <h2>Forex Market images</h2>
      <ImageCarousel images={images} />
    </div>
  );
};

export default App;
```
## imagecarousel.jsx
```
import React, { useState, useEffect } from 'react';

const ImageCarousel = ({ images }) => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prev) => (prev + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, [images.length]);

  return (
    <div className="carousel">
      <img src={images[currentIndex]} alt={`Slide ${currentIndex}`} />
      <div className="controls">
        <button onClick={prevImage}>⟨ Prev</button>
        <button onClick={nextImage}>Next ⟩</button>
      </div>
    </div>
  );
};

export default ImageCarousel;
```
## index.css
```
import React, { useState, useEffect } from 'react';

const ImageCarousel = ({ images }) => {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prev) => (prev + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prev) => (prev - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, [images.length]);

  return (
    <div className="carousel">
      <img src={images[currentIndex]} alt={`Slide ${currentIndex}`} />
      <div className="controls">
        <button onClick={prevImage}>⟨ Prev</button>
        <button onClick={nextImage}>Next ⟩</button>
      </div>
    </div>
  );
};

export default ImageCarousel;
```


## OUTPUT
![Screenshot 2025-05-01 231943](https://github.com/user-attachments/assets/34eb8da0-4901-457e-9d6b-dca4f25476c4)


## RESULT
The program for creating Image Carousel using React is executed successfully.
