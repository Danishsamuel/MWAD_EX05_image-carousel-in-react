# MWAD_EX05_image-carousel-in-react
## Date:26.10.25

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
ImageCarousel.js
```
import React, { useState, useEffect } from "react";
import "./ImageCarousel.css";

const ImageCarousel = () => {
  
  const images = [
    "https://picsum.photos/id/1018/800/400",
    "https://picsum.photos/id/1021/800/400",
    "https://picsum.photos/id/1025/800/400",
    "https://picsum.photos/id/1035/800/400",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval); 
  }, []);

  return (
    <div className="carousel-container">
      <div className="carousel">
        <img src={images[currentIndex]} alt="carousel" className="carousel-image" />
        <button className="prev-btn" onClick={prevImage}>❮</button>
        <button className="next-btn" onClick={nextImage}>❯</button>
      </div>

      <div className="indicators">
        {images.map((_, index) => (
          <span
            key={index}
            className={`dot ${index === currentIndex ? "active" : ""}`}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
};

export default ImageCarousel;
```
ImageCarousel.css
```

import React, { useState, useEffect } from "react";
import "./ImageCarousel.css";

const ImageCarousel = () => {
  
  const images = [
    "https://picsum.photos/id/1018/800/400",
    "https://picsum.photos/id/1021/800/400",
    "https://picsum.photos/id/1025/800/400",
    "https://picsum.photos/id/1035/800/400",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval); 
  }, []);

  return (
    <div className="carousel-container">
      <div className="carousel">
        <img src={images[currentIndex]} alt="carousel" className="carousel-image" />
        <button className="prev-btn" onClick={prevImage}>❮</button>
        <button className="next-btn" onClick={nextImage}>❯</button>
      </div>

      <div className="indicators">
        {images.map((_, index) => (
          <span
            key={index}
            className={`dot ${index === currentIndex ? "active" : ""}`}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
};

export default ImageCarousel;
```
App.js
```
import React from "react";
import ImageCarousel from "./ImageCarousel";

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
<img width="1884" height="1059" alt="Screenshot 2025-10-26 210846" src="https://github.com/user-attachments/assets/59438cb7-18de-4797-adeb-1882054a025f" />
<img width="1897" height="1046" alt="Screenshot 2025-10-26 210831" src="https://github.com/user-attachments/assets/51c13ea1-32fd-49b4-a76a-8675d45c2079" />
<img width="1891" height="1012" alt="Screenshot 2025-10-26 210908" src="https://github.com/user-attachments/assets/16a97c22-0335-4cc2-9c33-65f873942aed" />
<img width="1888" height="1033" alt="Screenshot 2025-10-26 210859" src="https://github.com/user-attachments/assets/ad755695-60a3-4a4e-b18c-cd16176d24b0" />





## RESULT
The program for creating Image Carousel using React is executed successfully.
