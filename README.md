# Tongdo Fantasia

통도환타지아는 대한민국 양산시에 위치한 놀이공원으로 아쿠아환타지아 워터파크가 함께 입지하고 있습니다.<br>
이러한 브랜드 특성을 반영하기 위해서 대표컬러를 파란색으로 선정했으며 해당색상이 주는 활력과 안정감을 고려하여 깔끔하고 직선적인 서체를 사용했습니다.
컨텐츠를 카드UI로 구성하고 상단에 검색영역을 추가하여 사용자의 접근성과 시인성을 높였습니다.

- [통도환타지아 홈페이지](https://www.fantasia.co.kr/main.htm)
- [통도환타지아 리뉴얼 페이지](http://yeji-jung.com/project/tongdo/index.html)

###### * *리뉴얼 페이지는 구글 크롬 브라우저에 최적화되어 있습니다.* ######

## 메인 페이지 ##

#### 1. 메인 비주얼 이미지 : Swiper 플러그인을 사용하여 이미지가 자동으로 슬라이드 되도록 작업했습니다. ####

![main](https://user-images.githubusercontent.com/74514595/113656346-aaf0af00-96d6-11eb-91aa-3759db5905ac.jpg)

    var mainVisual = new Swiper('.section .main_visual .swiper-container', {
            centeredSlides: true,
            autoplay: {
              delay: 3500,
              disableOnInteraction: false,
            },
            loop:true,
            pagination: {
              el: '.main_visual .swiper-pagination',
              clickable: true,
            },
            navigation: {
              nextEl: '.main_visual .swiper-button-next',
              prevEl: '.main_visual .swiper-button-prev',
            },
        });
      
      
#### 2. GNB : 마우스를 올리면 2depth가 나타납니다. 2depth에 직선이 양 옆으로 길어지는 트랜지션을 적용했습니다. ####

![GNB](https://user-images.githubusercontent.com/74514595/113657238-7978e300-96d8-11eb-94e0-1c0deeb99b9f.jpg)

    var gnb = $("#gnb > li"),
        gnbBg = $(".gnbwrap  #gnb > li > .gnbBg");
        
        gnb.mouseenter(function(){
            gnbBg.stop().slideDown();
        });
        gnb.mouseleave(function(){
            gnbBg.stop().slideUp();
        });
    
    #header nav .gnbwrap #gnb > li > .gnbBg > .depth2 > li:hover a:before{transform: scaleX(1);}
    #header nav .gnbwrap #gnb > li > .gnbBg > .depth2 > li > a:before{content: ""; display: block; position: absolute; left: 0; bottom: -3px; width: 100%; height: 2px; background-color: #000062; transform: scaleX(0); transform-origin: center; transition: transform 0.4s ease; z-index: 5;}


#### 3. 상단아이콘 : 돋보기 아이콘을 클릭하면 검색영역이 슬라이드 되며<br> 유저 아이콘에 마우스를 올리면 로그인 영역이 슬라이드 됩니다. ####

![search](https://user-images.githubusercontent.com/74514595/113657898-e9d43400-96d9-11eb-9f45-7a454248329b.jpg)

    var srchBtn = $("#header .search"),
        closBt = $("#header .closeBtn"),
        member = $("#header nav .gnbRight p.member"); 

        srchBtn.click(function(){
            $(".srchArea").slideDown(400);
        });
        closBt.click(function(){
            $(".srchArea").slideUp(400);
        });

        member.mouseenter(function(){
            $(this).children(".memberJoin").stop().slideDown();
        });
        member.mouseleave(function(){
            $(this).children(".memberJoin").stop().slideUp();
        });
        
#### 4. 환타지아 뉴스티커 : 코드펜 사이트를 참고했으며 공지사항이 한 줄씩 자동으로 나타납니다. ####       

![news](https://user-images.githubusercontent.com/74514595/113662482-26f0f400-96e3-11eb-8c7c-97a304b2bcc6.jpg)


        $(function(){
                $('#newsticker2').Vnewsticker({
                  speed: 700,         
                  pause: 2500,       
                  mousePause: true,  
                  showItems: 1,    
                  direction : "Up" 
                });
            });  ...
            
출처 : https://codepen.io/eond/pen/NqEEez

#### 5. 할인혜택 : Swiper 플러그인을 사용하여 가운데 박스의 사이즈가 변하도록 구현했습니다.<br> 우측 + 버튼에 마우스를 올리면 더보기 글자가 슬라이드 됩니다. ####

![con1](https://user-images.githubusercontent.com/74514595/113659292-ac24da80-96dc-11eb-83ca-2c2a9ea297c7.jpg)

    var sec1Swiper = new Swiper('.main_con1 .swiper-container', {
            slidesPerView: 3,
            direction: getDirection(),
            loop:true,
            navigation: {
              nextEl: '.main_con1 .swiper-button-next',
              prevEl: '.main_con1 .swiper-button-prev',
            },
            on: {
              resize: function () {
                swiper.changeDirection(getDirection());
              }
            }
        });
        
    .section2 .main_con1 .moreBtn a{position: absolute; left: 0; top: 0; width: 60px; padding-top: 45px; font-size: 14px; font-weight: 700; line-height: 16px; color: #444; text-align: center; opacity: 0;}
    .section2 .main_con1 .moreBtn:hover a{top: 15px; left: -5px; transition: top .4s ease-in-out; opacity: 1;}


#### 6. 어트랙션 : 탭 버튼을 클릭하면 해당 컨텐츠로 변경됩니다. ####

![attrac](https://user-images.githubusercontent.com/74514595/113660236-9f08eb00-96de-11eb-954e-1f2a12b8815d.jpg)

    var $mainTit = $('.main_sec2 .main_tit h2'),
        $night = $('.main_sec2 .main_tit h2.night'),
        $child = $('.main_sec2 .main_tit h2.child');

    let $tabMenu = $('.main_sec2 .tab_btn p'),
        $tabnight = $('.main_sec2 .tab_btn p.night'),
        $tabchild = $('.main_sec2 .tab_btn p.child'),
        $tabCon = $('.main_sec2 .main_con2 .list');

        $tabMenu.on('click',function(e){
            e.preventDefault(); 

            let _href = $(this).children('a').attr('href');
            $tabCon.hide();
            $( _href ).show();
            
            $tabMenu.removeClass('on');
            $(this).addClass('on');

            $mainTit.hide();
            if($tabnight.hasClass('on')){
                $night.show();
            }else if($tabchild.hasClass('on')){
                $child.show();
            }
    });

#### 7. 공지사항 : Swiper 플러그인을 사용하여 페이지 번호와 버튼을 클릭하면 슬라이드 되도록 구현했습니다. ####

![notice](https://user-images.githubusercontent.com/74514595/113660636-83521480-96df-11eb-9977-636bb4bca2f0.jpg)

      var sec4Swiper = new Swiper('.main_sec4 .swiper-container', {
              slidesPerView: 4,
              spaceBetween: 30,
              loop:false,
              pagination: {
                el: '.main_sec4 .swiper-btWrap .swiper-pagination',
                clickable: true,
              },
              navigation: {
                  nextEl: '.main_sec4 .swiper-btWrap .swiper-button-next',
                  prevEl: '.main_sec4 .swiper-btWrap .swiper-button-prev',
              },
          });

#### [리뉴얼 페이지](http://yeji-jung.com/project/tongdo/index.html)에 직접 방문하셔서 살펴보세요. ####
