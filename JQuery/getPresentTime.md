Get present time function
```javascript
   //현재 시간을 가져오는 함수

        $.getPresentTime = function () {

            let date = new Date();

            let year = date.getFullYear();

            let month = ('0' + (

                date.getMonth() + 1

            )).slice(-2);

            let day = ('0' + date.getDay()).slice(-2);

            let dateStr = year + '-' + month + '-' + day;

  

            let dateKo = date.toLocaleString('ko-kr');

  

            console.log(dateStr);

            console.log(dateKo)

            // console.log('수강 시작 시간 :' + date.toLocaleString('ko-kr'));

  

            return dateKo;

        };
```


GetVideoUrl
```javascript
        /* Video Play Box - 2*/

            $.each(urlList, function (index, item) {

  

                let Videom4v = item.m4v

                let videoposter = item.poster

  
  

                $('.test1')

                    .append($('<button>').prop({

                        id: `video${index}`, innerHTML: `Video-${index + 1}`, className: 'getvideo', value:

                            Videom4v + '**' + videoposter, style:'margin : 10px'

                    }))

            })

  
  

            $('.getvideo').click(function (e) {

                // console.log(e.target.value)

                let url = e.target.value

                let murl = url.split('**')

                // console.log(murl)

                $("#jquery_jplayer_1").jPlayer("clearMedia");

                $("#jquery_jplayer_1").jPlayer("setMedia", {

                    m4v: murl[0],

                    poster: murl[1]

                });

            })
```

#JQuery