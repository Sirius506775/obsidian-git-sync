```javascript

    //jPlayer 재생시간 제어 이벤트

            $("#jquery_jplayer_1").bind($.jPlayer.event.timeupdate, function (event) {

                let currentTime = Math.floor(event.jPlayer.status.currentTime)

                if (!event.jPlayer.status.paused) {

  

                    // console.log("현재 재생시간 : " + event.jPlayer.status.currentTime)

  

                    let Stime = event.jPlayer.status.currentTime

  

                    // console.log(Stime)

  

                }

  

                //동영상 재생시간 출력

                $(".timeStr").text(

                    $.jPlayer.convertTime(parseInt(event.jPlayer.status.currentTime)) + "/" + $.jPlayer.convertTime(parseInt(event.jPlayer.status.duration))

                );

  

                //재생시간 5초 이후

                $(".next").click(function () {

                    $("#jquery_jplayer_1").jPlayer("play", event.jPlayer.status.currentTime + 5);

                });

  

                //재생시간 5초 이전

                $(".prev").click(function () {

                    $("#jquery_jplayer_1").jPlayer("play", event.jPlayer.status.currentTime - 5);

                });

  

            });
```


Jplayer에서 재생 속도 제어를 하


---

#### 배속 기능 만들기
비디오의 배속 기능을 만들면서, 직접적으로 영상 재생을 실행하고 있는 노드를 컨트롤할 필요가 있었다 .

JPlayer docs에서 재생 속도를 컨트롤하는 메소드는 playbackRate를 

크롬 콘솔 유틸리티 API 레퍼런스(https://developer.chrome.com/docs/devtools/ )를 한 번 살펴볼 필요성을 느끼게 되었다. 

Chrome Dev Tools에서 힌트를 얻을 수 있었다.


querySelector로 받아오기 힘든 elements인 경우 노드가 엄청 많아서 원하는 부분만을 선택하기가 힘들었다.
이때 $0를 사용하면 유용하다. 

$0은 Elements 탭에서 가장 최근에 선택한 element(또는 profile panel object)의 레퍼런스다.

$1, $2, $3, $4도 사용 가능한데, 이것은 1~4번째 전에 선택한 Element의 레퍼런스를 나타냅니다

```javascript
 //재생속도 배속 이벤트

            const video = $("#jp_video_0")[0]

  

            $(".speed_default").click(function(){

                video.playbackRate = 1

                console.log(`재생속도 : ${video.playbackRate} 배속`)

            })

  

            $(".speed_2x").click(function(){

                video.playbackRate = 2

                console.log(`재생속도 : ${video.playbackRate} 배속`)

            })

  

            $(".speed_3x").click(function(){

                video.playbackRate = 3

                console.log(`재생속도 : ${video.playbackRate} 배속`)

            })
```


#JQuery
