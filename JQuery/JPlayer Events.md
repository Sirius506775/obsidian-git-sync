##### 버튼 색상 컨트롤

```javascript
  

    //버튼 색상 컨트롤(Size, Bar Control)

    let sizeBtn = document.querySelectorAll(".sizeBtn");

    let onOff = document.querySelectorAll(".onOff");

    let speedBtn = document.querySelectorAll(".speedBtn");

  

    //SizeBtn 색상 변경 이벤트

    function handleClick(event) {

        // console.log(event.target);

        // console.log(this);

        // 콘솔창을 보면 둘다 동일한 값이 나온다

  

        // console.log(event.target.classList);

  

        if (event.target.classList[1] === "clicked") {

            event.target.classList.remove("clicked");

        } else {

            for (var i = 0; i < sizeBtn.length; i++) {

                sizeBtn[i].classList.remove("clicked");

            }

  

            event.target.classList.add("clicked");

        }

    }

    //onOffBtn 색상 변경 이벤트

    function handleClick1(event) {

  

        if (event.target.classList[1] === "clicked") {

            event.target.classList.remove("clicked");

        } else {

            for (var i = 0; i < onOff.length; i++) {

                onOff[i].classList.remove("clicked");

            }

  

            event.target.classList.add("clicked");

        }

    }

    //speedBtn 색상 변경 이벤트

    function handleClick2(event) {

  

        if (event.target.classList[1] === "clicked") {

            event.target.classList.remove("clicked");

        } else {

            for (var i = 0; i < speedBtn.length; i++) {

                speedBtn[i].classList.remove("clicked");

            }

  

            event.target.classList.add("clicked");

        }

    }

  

    function init() {

        for (var i = 0; i < sizeBtn.length; i++) {

            sizeBtn[i].addEventListener("click", handleClick);

        }

        for (var i = 0; i < onOff.length; i++) {

            onOff[i].addEventListener("click", handleClick1);

        }

        for (var i = 0; i < speedBtn.length; i++) {

            speedBtn[i].addEventListener("click", handleClick2);

        }

  

    }

  

    init();

```

##### 제어 인터페이스 Hide
```javascript
/* 컨트롤 인터페이스 숨기기 (to use hide() */

            $(".jp-hide").click(function () {

                let button = $(".constrol-button").css('display')

  

                if (button !== 'none') {

                    $(".constrol-button").hide(function () {

                        // button = 'hide';

                        console.log(button)

                    });

                } else {

                    $(".constrol-button").show(function () {

                        // button = 'show';

                        console.log(button)

                    })

                }

  

            })
```

##### 비디오 클릭 시 재생 및 일시정지
```javascript
// 비디오 클릭 시 재생 및 일시정지

            let flg = false;

            $("#jquery_jplayer_1").bind($.jPlayer.event.click, function () {

                if (flg !== true) {

                    $(".jp-jplayer").jPlayer("play");

                    flg = true;

                } else {

                    $(".jp-jplayer").jPlayer("pause");

                    flg = false;

                }

                // console.log(flg);

            });
```

##### 프레임 사이즈 제어
```javascript
  

            //프레임 사이즈 제어 이벤트

            //270px

            $(".option_sizeFull_270p").click(function () {

                $("#jquery_jplayer_1").jPlayer({

                    size: {

                        width: "480px",

                        height: "270px",

                        cssClass: "jp-video-270p"

                    }

                });

                return false;

            });

            //360px

            $(".option_sizeFull_360p").click(function () {

                $("#jquery_jplayer_1").jPlayer({

                    size: {

                        width: "640px",

                        height: "360px",

                        cssClass: "jp-video-360p"

                    }

                });

                return false;

            });

            //Full

            $(".option_sizeFull_full").click(function () {

                $("#jquery_jplayer_1").jPlayer({

                    size: {

                        width: "100%",

                        height: "94%",

                        cssClass: "jp-video-full"

                    }

                });

                return false;

            });
```

##### 플레이어 재생시간 제어 

```javascript
//jPlayer 재생시간 제어 이벤트

            $("#jquery_jplayer_1").bind($.jPlayer.event.timeupdate, function (event) {

                let currentTime = Math.floor(event.jPlayer.status.currentTime)

                if (!event.jPlayer.status.paused) {

  

                    // console.log("현재 재생시간 : " + event.jPlayer.status.currentTime)

  

                    let Stime = event.jPlayer.status.currentTime;

  

                    // console.log(Stime)

  

                };

                //동영상 재생시간 화면 출력

                $(".timePrint").text(

                    $.jPlayer.convertTime(parseInt(event.jPlayer.status.currentTime)) + "/" + $.jPlayer.convertTime(parseInt(event.jPlayer.status.duration))

                );

  

                //Next 버튼 클릭 시 재생시간 5초 이후

                $(".next").click(function () {

                    $("#jquery_jplayer_1").jPlayer("play", event.jPlayer.status.currentTime + 5);

                });

  

                //Prev 버튼 클릭 시 재생시간 5초 이전

                $(".prev").click(function () {

                    $("#jquery_jplayer_1").jPlayer("play", event.jPlayer.status.currentTime - 5);

                });

  

            });
```

##### 동영상 재생 컨트롤

```javascript
//동영상 재생 시작 시 시간 출력

            $("#jquery_jplayer_1").bind($.jPlayer.event.play, function () {

  

                let a = $('.startDate').text()

  

                if (a == '') {

                    $('.startDate').text("시작 시간 : " + $.getPresentTime())

                } else {

                    return

                }

            });

            //동영상 일지정지 시 시간 출력

            $("#jquery_jplayer_1").bind($.jPlayer.event.pause, function (event) {

                beforeCurrentTime = currentTime;

                $('.pauseDate').text("일시중지 시간 : " + $.getPresentTime());

                pauseDate = $.getPresentTime();

                console.log("beforeCurrentTime:" + beforeCurrentTime)

            });

            //동영상 중단 시 시간 출력

            $(".jp-stop").on("click", function (event) {

                $('.stopDate').text("중단 시간 : " + $.getPresentTime());

                stopDate = $.getPresentTime();

                // let text = $('.stopDate').text()

  

                //  if(text === ''){

                //      $('.stopDate').text("종료 시간 : " + $.setDate())

                //  }

                //  else{

                //      return          

                //  }

            });

            //동영상 종료 시 시간 출력

            $("#jquery_jplayer_1").bind($.jPlayer.event.ended, function () {

                let a = $('.endDate').text()

  

                if (a == '') {

                    $('.endDate').text("종료 시간 : " + $.getPresentTime())

                } else {

                    return

                }

            });
```