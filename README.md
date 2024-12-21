# vue-js-modal 라이브러리 정리

vue-js-modal 라이브러리 1.3.35에서는 fade 효과가 적용되지 않는다.
각 버전의 node_module/vue-js-modal/dist/index.js에서 속성들을 찾아보면 다음과 같다.  
(webpacking 되어있어 Ctrl F로 찾아봐야 한다.)

- 1.3.35v
  - `transition`: "fade"
  - `overlayTransition`: "overlay-fade"
  ```js
  this.$modal.show(DynamicModal, {
    // overlayTransition: 'overlay-fade',
    overlayTransition: '', // 효과를 끌 떄 공백
    transition: "fade"
  })
  ```

- 2.0.1v
  - `transition`: "vm-transition--modal"
  - `overlayTransition`: "vm-transition--overlay"
  ```js
  this.$modal.show(DynamicModal, {
    // overlayTransition: 'vm-transition--overlay',
    overlayTransition: '', // 효과를 끌때 공백
    transition: "vm-transition--modal"
  })
  ```

## 예외 사항

`1.3.35 버전`의 경우 overlay-fade관련 css 선택자 외에도 nice-modal-fade 라는 css선택자가 존재한다.   
그러나 해당 선택자에 대한 transition css효과는 node_module/vue-js-modal/dist/index.js 파일에 정의되어있지 않다.  
transition: "fade"(String) 라는 css선택자에 대한 효과또한 정의되어 있지 않다.  
뜬금없는 nice-modal이라는 명칭은, vue-nice-modal 이라는 다른 라이브러리로 유추된다.  

`2.0.1 버전`의 경우 Pure Bootstrap과 함께 사용시 페이드 효과가 전혀 작동되지 않으며,  
모달창이 깜-빡이면서 출력되는 충돌현상이 있다.  
(해당 현상에 대한 대안책 모색중....)