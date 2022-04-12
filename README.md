# React를 이용해서 Slider 만들기

### 앞으로 많은 프로젝트에서 만들 slider 연습하기

### react hook을 사용해서 상태 컨트롤 하기

### App.jsx
```
import "./App.css";
import { motion } from "framer-motion";
import { useRef, useEffect, useState } from "react";
import images from "./images";

function App() {
  const [width, setWidth] = useState(0);
  const carousel = useRef();

  useEffect(() => {
    setWidth(carousel.current.scrollWidth - carousel.current.offsetWidth);
  }, []);

  return (
    <div className="App">
      <motion.div
        ref={carousel}
        className="carousel"
        whileTop={{ cursor: "grabbing" }}
      >
        <motion.div
          drag="x"
          dragConstraints={{ right: 0, left: -width }}
          className="inner-carousel"
        >
          {images.map((image) => {
            return (
              <motion.div className="item" key={image}>
                <img src={image} alt="" />
              </motion.div>
            );
          })}
        </motion.div>
      </motion.div>
    </div>
  );
}

export default App;
```
