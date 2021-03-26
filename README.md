# Ex.RobotBasic

#01/09/2019
Beginning Robot

#Command for installation.


    Pip install robotframework-databaselibrary
    Pip install ypmysql
    Pip install robotframework selenium2library
    Pip freeze
    pip install robotframework ...
	     robot --version
       pybot --version
    Python -m pip install --upgrade pip
    Pip install webdriver-manager
    Pip show robotframework
    Pip install pymssql
    Pyton --version
    robot --version
    
    
#Suggestion a little bit.


	- Version Browser ที่จะใช้ต้องตรงกันกับ Driverที่ลง และ ติดเรื่อง UTF-8  เอาไปเพิ่ม X:location drive\Programs\Python\Python37-32\Lib\encodings\ailases  874


#Basic for write script test case    4 section 


#รวมทั้ง 4 section เข้าด้วยกัน เราจะได้ไฟล์ test script ที่ชื่อว่า test.robot (จะตั้งเป็น .txt ก็ได้ เอาตามสะดวกเลย) ตามนี้
* Setting >กำหนด file และ library สำหรับ เทสสคริปต์ ใช้อ้างอิง
* Keyword >ชุดคำสั่ง เรียกใช้ที่กำหนดในVariables และ Testcase
* Variables >การประการตัวแปรที่ใช้งานได้ซ้ำๆ ใช้ในส่วน Keywords ,Testcase ที่อยู่ใน Format    " ${ชื่อตัวแปร} "
* Test Cases >ที่จะให้ทำงานตามลำดับ



#คำสั่ง Run File  Go to fileLocation and runcommad in cmd >X:Xpath/Xpath/Xpath/robot filename.txt >Enter



#Example  Open Chorme

  
    *** Settings ***
    Library    Selenium2Library

    *** Variable ***
    ${url}        http://www.google.com
    ${browser}        Chrome

    *** Test Cases ***
    Go To GoogleSuite
      Open Browser	${url}		${browser}
    จะเห็นได้ว่าไม่จำเป็นต้องกำหนด Variable เพราะว่าลำดับเคสที่เราจะเทสมีแค่ 1 ลำดับ





#Example  Open Page Facebook and [has config value in variable] and keyword[adsign argument].


    *** Settings ***
    Library    Selenium2Library
    Library    BuiltIn
    Library    String
    Suite Teardown     Close Browser

    *** Variable ***
    ${url_facebook}        https://www.facebook.com
    ${title_facebook}      Facebook - เข้าสู่ระบบหรือสมัครใช้งาน
    ${input_user}          //*[@id="email"]
    ${input_pass}          //*[@id="pass"]
    ${btn_login}           //*[@id="loginbutton"]
    ${username_fail}            iamgique@iamgique.com
    ${password_fail}            iamgique@iamgique.com
    ${username_success}             EmailAddress@xxxxmail.com
    ${password_success}             12345678

    *** Keywords ***
    Open Browser facebook.com
      Open Browser ${url} ${browser}

    Verify facebook page
        [Arguments]                ${title}
        Title Should Be            ${title}
    Input Username and Password
         [Arguments]      ${xpath_user}       ${xpath_pass}     ${username}       ${password}
         Element Should Be Visible    ${xpath_user}
         Element Should Be Visible    ${xpath_pass}
         Input Text       ${xpath_user}       ${username}
         Input Text       ${xpath_pass}       ${password}
    Click Button Login
         [Arguments]       ${btn}
         Element Should Be Visible    ${btn}
         Click Element        ${btn}
    Verify Login Fail
       [Arguments]        ${xpath}
       Element Should Be Visible        ${xpath}
    Verify Login Success
       [Arguments]        ${xpath}
       Element Should Be Visible        ${xpath}

    *** Test Cases ***
    Login facebook - Fail
        [tags]    fail
        Open Browser    about:blank    chrome
        Go To           ${url_facebook}
        Verify facebook page           ${title_facebook}
        Input Username and Password    ${input_user}     ${input_pass}       ${username_fail}      ${password_fail}
        Click Button Login          ${btn_login}
    Login facebook - success
        [tags]    success
        Open Browser    about:blank    chrome
        Go To           ${url_facebook}
        Verify facebook page           ${title_facebook}
        Input Username and Password    ${input_user}     ${input_pass}       ${username_success}      ${password_success}
        Click Button Login             ${btn_login}

    เมื่อ Run fileFackebook.txt Robot จะอ่านไฟล์แบบ Interpreiter อ่านทุกบรรทัดจากบนลงล่าง

Comment in Robot #content


#Google Serach and has time[set time to wait for process],setup teardown[closed browser when end process]
เมื่อมี testcase 



	*** Settings ***
	Library    Selenium2Library
	Library    BuiltIn
	Library    String
	Library	   RequestsLibrary
	Suite Teardown     Close Browser

	*** Variable ***
	${url}        http://www.google.com
	${browser}        Chrome
	${search}			Food for Vegetable?
	${inputtext}			5
	*** Keywords ***
	Open browser Chrome
			[Arguments]	${browser}	${url}
			Open browser		${browser}			${url}
	Search info
			[Arguments]				${search}
			Input Text		name=q				${search}
	Wait for result
			Wait Until Page Contains		${inputtext}		5 seconds			food for vegetables

	*** Test Cases ***
	Open Browser
	    Open Browser  ${url}		${browser}
	Search info
		Input Text				name=q			   ${search}
	Wait for Search Results
	    Wait Until Page Contains		${inputtext}		5 seconds			Food for Vegetable?		




#Test case Only can be run!!



	*** Test Cases ***
	Go To GoogleSuite
		LOG         Hi! My Robot
	
	
	*** Settings *** 
	Library Selenium2Library 
	Library BuildIn Library 
	String Library RequestLibrary

	*** Variable *** 
	${url} http://
	${browser} Chrome 
	${title} ASH-BPO 
	${Selected} //[@id="UserId_chosen"] 
	${Search} IC000001 
	${MouseDown} xpath=//li[contains(.,'${Search}')] 
	${button} //[@id="headingOne"]
	${Select} //*[@id="navbar"] 
	${OpenMenu} Log Management 
	${Mouse Down} xpath=//li[contains(.,'${OpenMenu}')]

	*** Keywords *** 
	Go To ASH-BPOsuite 
	Open Browser ${url} ${browser}

	View to title 
	[Argruments] ${title} 
	Title Should Be ${title}

	Selected to data 
	[Argruments] ${Selected} ${Search} 
	Click Element ${Selected} 
	Page Should Contain Element ${Selected}

	Search to data
	[Argruments] ${Search} 
	Input Text IC000001 
	Page Should Contain Input Text IC000001 50s

	Click Contians 
	[Argruments] ${MouseDown} 
	Page Should Contain Element ${MouseDown} 
	Click Element ${MouseDown}

	Click data 
	[Argruments] ${button} 
	Page Should Contain Element //*[@id="headingOne"] 
	Click Element ${button}

	Select to data 
	[Argruments] ${Select} 
	Click Element ${Select} 
	Page Should Contain Element Log Management 70s

	Open Menu 
	[Argruments] //*[@id="navbar"] ${OpenMenu} 
	Input Text Log Management 
	Page Should Contain Input Text Log Management 70s

	Click Contians 2 
	[Argruments] ${Mouse Down} 
	Page Should Contain Element ${Mouse Down} 50s 
	Click Element ${Mouse Down}

	*** Test Cases *** 
	Go To ASH-BPOsuite 
	Open Browser ${url} ${browser}

	View to title 
	Title Should Be ${title}

	Selected to data Click Element ${Selected} 
	Page Should Contain Element ${Selected} 50s

	Search to data
	Input Text IC000001 
	Page Should Contain Input Text IC000001 50s

	Click Contians 
	Page Should Contain Element ${MouseDown} 50s 
	Click Element ${MouseDown}

	Click Data 
	Page Should Contain Element //*[@id="headingOne"] 50s 
	Click Element ${button}

	Search to data
	Input Text IC000001 
	Page Should Contain Input Text IC000001 50s

	Choese to data 
	Click Element ${Select} 
	Page Should Contain Element Log Management 70s

	Open Menu 
	Input Text Log Management 
	Page Should Contain Input Text Log Management 70s

	Click Contians 2 
	Page Should Contain Element ${Mouse Down} 50s 
	Click Element ${Mouse Down}

  
  
