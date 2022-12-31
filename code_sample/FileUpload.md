```js
import axios from "axios";

import React from "react";

import { useRef } from "react";

import { useState } from "react";

  

const removeFileToServer = async (fileName) => {

  const res = await axios.post(`http://localhost:8080/delete`, "fileName=" + fileName,  {

    headers: {"Content-Type": "application/x-www-form-urlencoded"},

  });

  return res.data;

};

  

const uploadToServer = async (formObj) => {

  const res = await axios.post("http://localhost:8080/upload1", formObj, {

    headers: { "Content-Type": "multipart/form-data" },

  });

  return res.data;

};

  

const FileUpload = () => {

  const [requestList, setRequestList] = useState([]);

  

  const uploadValue = useRef();

  

  //upload 버튼 클릭 시 이벤트

  const uploadHanlder = () => {

    console.log("---------uploadHanlder Running-----------------");

    const formObj = new FormData(); //form 데이터 객체 생성

    const realImg = uploadValue.current.files;

  

    for (let i = 0; i < realImg.length; i++) {

      formObj.append("files", realImg[i]); //formData 객체에 파일을 추가하기 위해 append(key,value) 사용

    }

  

    uploadToServer(formObj).then((res) => {

      setRequestList(res);

    });

  };

  

  //del 버튼 클릭 시 파일 삭제

  const removeFile = (uuid, link) => {

    const delFile = uuid;

    console.log("delFile : " + delFile);

  

    const newFileList = requestList.filter((data) => data.uuid !== delFile);

  

    removeFileToServer(link).then((res) => {

    });

    setRequestList(newFileList);

  };

  

  //업로드 파일 정보 화면 출력

  const reqList = requestList.map(({ uuid, fileName, thumbnail, link }) => (

    <li key={uuid}>

      <span>{fileName}</span>

      <button

        onClick={() => {

          removeFile(uuid, link);

        }}

      >

        X

      </button>

      <img

        src={`http://localhost:8080/view?fileName=${thumbnail}`}

        alt="fileName"

      />

    </li>

  ));

  

  return (

    <>

      <div>

        <h4>Default File Upload</h4>

          <input

            className="form-control"

            ref={uploadValue}

            onChange={uploadHanlder}

            type="file"

            name="realImg"

            accept="'image/*"

            multiple

          />

      </div>

      <ul>{reqList}</ul>

    </>

  );

};

  

export default FileUpload;
```