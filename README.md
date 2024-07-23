# jdsouza
This is my first github repo- practice

Playwright

	
	

About playwright

1. Playwright will support web browser , API , mobile browsers- but will not support the native mobile apps[real mobile device]
2. It supports - java, javascript/typescript , python .net
3. Browsers supported - chromium , webkit[safari] , Firefox 
4. It supports headless and headed [by default it. Supports headless]
5. Os supported - windows , Mac , linux
6. it has auto wait capability


Features of playwright
1. Free and open-source[no need to buy licence anybody can download and use]
2. Multiple languages , multiple browser , multiple OS
3. Easy set up and configuration
4. Automate API , Functional , supports accessibility testing
5. It has built-in reports
6. Supports CI/CD, Docker
7. Supports parallel testing , cross-browser testing
8. It has built auto wait [selenium doesn’t have - we use implicate , excplicit]
9. Has built- in assertions
10. Multi tab and multi window support
11. Frames , shadow DOM elements 
12. Support parameterisations
13. Inbuilt assertions [we don’t have to use the external assertions]

Advanced features:
1. Tracing and debugging - it provides automatic screens , video 
2. Time travelling is easy
3. It can take the cookies info and in incognito we can store those cookies[browser context management]
4. Codegen tool - we can write the code automatically by going through the steps

￼





Installation of playwright

Pre-requisites :
1. Nodejs - open source platform which is used to run the javascript - set the path variable
2. VScode editor

Installing the playwright for the project - using terminal
1. Open ua project folder [empty folder]and in console run npm init playwright@latest
2. Follow and fill all the necessary details
    1. npm playwright -v - gives the current version




Installing the playwright for the project - using vs code extension
1. Open the folder and click on extension and download playwright
2. Go to view -> playwright in test click on and project is ready



Structure of the playwright project

- node_modules - all the jars are installed- that is dependencies
- Tests - where we store all out testscripts
- Package.json - its like pom - where we store all our dependencies
- Playwright.config.js - where we run our test cases - path is given in that file , browsers are stored in that file



Command to execute/run the code:
- npx playwright test     — runs all the test cases that’s in headless mode
- npx playwright tests — headed	- it will run in headed mode[where browser will be opneed]
- npx playwright test BasicsTest.spec.js        - it will execute the specified file
- If you just want to execute in particular browsers
	npx playwright test BasicsTest.spec.js --project=chromium
- npx playwright test BasicsTest.spec.js --project=chromium --debug    - you can debug by this command, you will get the playwright inspector

To show the reports
npx playwright show-report


Why async/await required ?

Javascript is an asynchronous - it doesn’t execute in the order or sequence , even if the promise is not resolved it will move to the next step to overcome this we need to provide the promise by using the await and async methods
Every step of the code will return the promise - different state - - resolved , pending and rejected

To make the sequential execution we need to write the await async that it will return the resolve promise



Fixtures: global fixtures 
 that’s globally available in the scripts- we have fixtures
Fixtures will contain the the methods - through which we can automate the scripts
All the methods click, is displayed or any other methods - these methods will be available due to fixtures
const { test } = require("@playwright/test");

test("basics",async({browser})=>
{
    const context=await browser.newContext();
    const page=await context.newPage();
    page.goto("https://playwright.dev/docs/test-fixtures");

})

 Instead of using these 2 lines playwright has modified and we can just use the page - when we do not have to pass any parameters then only use the page

 const context=await browser.newContext(); - here new instance will be created without any cookies 
 const page=await context.newPage(); - new fresh page will be created

After modification


 test("without browser context by using page",async({page})=>
    {
        page.goto("https://playwright.dev/docs/test-fixtures")    
    })

We can change the browser name in config file

 

About configuration file


Section 3 : how to create the playwright test and run

2 ways 2 generate the scrips

1. We need to create our files inside the tests folder
2. Need to give name.spec.js as a extension


There are 2 ways where we can enter the values and the locators

Way1
 await page.locator("#input-firstname").fill("jonita");

Way2
  await page.fill("#input-lastname","Dsouza");


Customised Locators : 

- To  identify the elements on the webpage and perform actions on those locators

Types of locators supports
	1. Property 
	2. Css
	3. Xpath

About locators:  if we have multiple value for a locator and if you know that index is fixed and not changing then u can use the below options


Page.locator(“higher”).first();
Page.locator(“fhfg”).nth(0)
Page.locator(“fbhfgr”).last()


//if we give this method we will not get any value but since it is array, it will return the elements - so playwright will not know whether it return all the elements or not]

console.log(await page.locator('.card-body a').allTextContents());


1. Id - tag name#id or #id
2. Css - tag name.classname.   or .classname
3. Parent_name   Childnmae   - it is like traversing


When we have multiple locators : then use $$

example:
const links=await page.$$("a");



Build in playwright locators

1. Page.getByRole()
2. page.getByText()
3. Page.getByLabel()
4. Page.getByPlaceholderText()
5. Page.getByAltText()
6. Page.getByTitle()
7. Page.getByTestId()

1. Page.getByAltText()
		- if you have image alt text and want to verify if the image is present then we can use this




Assertions : there are done to perform the validations in the UI

List of assertion
await expect(locator).toBeAttached()	Element is attached
await expect(locator).toBeChecked()	Checkbox is checked
await expect(locator).toBeDisabled()	Element is disabled
await expect(locator).toBeEditable()	Element is editable
await expect(locator).toBeEmpty()	Container is empty
await expect(locator).toBeEnabled()	Element is enabled
await expect(locator).toBeFocused()	Element is focused
await expect(locator).toBeHidden()	Element is not visible
await expect(locator).toBeInViewport()	Element intersects viewport
await expect(locator).toBeVisible()	Element is visible
await expect(locator).toContainText()	Element contains text
await expect(locator).toHaveAccessibleDescription()	Element has a matching accessible description
await expect(locator).toHaveAccessibleName()	Element has a matching accessible name
await expect(locator).toHaveAttribute()	Element has a DOM attribute
await expect(locator).toHaveClass()	Element has a class property
await expect(locator).toHaveCount()	List has exact number of children
await expect(locator).toHaveCSS()	Element has CSS property
await expect(locator).toHaveId()	Element has an ID
await expect(locator).toHaveJSProperty()	Element has a JavaScript property
await expect(locator).toHaveRole()	Element has a specific ARIA role
await expect(locator).toHaveScreenshot()	Element has a screenshot
await expect(locator).toHaveText()	Element matches text
await expect(locator).toHaveValue()	Input has a value
await expect(locator).toHaveValues()	Select has options selected
await expect(page).toHaveScreenshot()	Page has a screenshot
await expect(page).toHaveTitle()	Page has a title
await expect(page).toHaveURL()	Page has a URL
await expect(response).toBeOK()	Response has an OK status



Negative assertions :  await  expect(malecheckbox).not.toBeChecked();
Use .not  before every assertion function




Hard assertions vs soft assertions


Hard assertions - If the assertions fails - then the code/ execution will be terminated

Soft assertions - if the assertions fails - then the code will continue and it will thro terror in the reports , it makes the test as failed even though execution is continued and completed

	example
		await expect.soft(locator).toBeAttached()






UI actions 

1. Input box


fill() - is used to enter the values

validations

const username= await page.locator("#input-email")
await expect(username).toBeVisible();
await expect(username).toBeEmpty();
await expect(username).toBeEditable();
await expect(username).toBeEnabled();
await page.locator("#input-email").fill("jo123@gmail.com")



2. RadioButtons and checkbox [both validations looks same - check()]

Validations

 await page.goto("https://practice.expandtesting.com/radio-buttons")
 const footballradioBtn= await page.locator("#football")
 await footballradioBtn.check();
 await expect(footballradioBtn).toBeChecked();
 expect (await page.locator("#football").isChecked()).toBeTruthy();



Checking the multiple checkbox
1. Store the values into array/objects that you want to check/select
2. Iterarte through it and select it



check()
uncheck()



3. How to handle the dropdown
	1. Using select tag
 These are the different way to select the  SELECT tag drop-down:
// await page.locator("#country").selectOption({label:"India"})
// await page.locator("#country").selectOption('India')
 const countryName=await page.locator("#country").textContent();
 await expect(countryName.includes("India")).toBeTruthy();
//await page.locator("#country").selectOption({value:"brazil"})
 await page.locator("#country").selectOption({index:3})




	2. Without select tag

		if there is no select tag 
		example:
		const options = await page.$$("#country option")

for(const option of options)
  {
    const text= await option.textContent()

    if(text.includes("India"))
      {
        await page.selectOption("#country",text)
      }
  }
await page.waitForTimeout(4000)





4. How to handle the multi select dropdown- select tag
	- We can store it in array and select the multiple values
await page.goto("https://testautomationpractice.blogspot.com/")
  await page.selectOption("#colors",['Blue','Red','Yellow'])
  await page.waitForTimeout(4000)
  const locs= page.locator("#colors option")
  await expect(locs).toHaveCount(5)



5. How to handle the bootstrap dropdown - without select option


await page.goto("https://www.jquery-az.com/boots/demo.php?ex=63.0_2#google_vignette")
  await page.locator("button.multiselect").click()
  const option = await page.$$("ul>li label")

  for(let options of option)
    {
    const values= await  options.textContent()
    if(values.includes('Angular')|| values.includes('Java'))
      {
       await options.click()
      }
    }




6. Handle autosuggestion dropdown

	- providing the few character in the input field and searching for the data

Example:
await page.goto("https://www.amazon.in/")
  //const searchInputSelector = '#nav-search-bar-form'; 
  const field=page.locator("#nav-search-bar-form")
 //await field.click()
  await page.locator("#twotabsearchtextbox").fill("pen")
  await page.waitForTimeout(1000)
  let suggestionFound = false;

  const text=await page.$$(".s-suggestion-container")
  await page.waitForSelector('.s-suggestion-container');

  for (const options of text)
    {const textPage= await options.textContent()
      if(textPage.includes("pen drive"))
        {
         await  options.click()
          suggestionFound = true;
          break;
          
        }


    }
    expect(suggestionFound).toBe(true);



7. Handle the hidden suggestions
 
Pending



8.Handling the alert

1. Playwright will automatically handle the alert dialogues 
2. We need to handle the alert first and then click on Ok on the alert
3. We can perform and validate the alert

This is how we handle the alert before clicking on it
page.on('dialog',async dialog=>
  {
  
    expect(dialog.type()).toContain('confirm')
    expect(dialog.message()).toContain("Press a button!")
    await dialog.dismiss()
  
  })

  await page.locator("//button[text()='Confirm Box']").click()
  expect(page.locator("#demo")).toHaveText("You pressed Cancel!")



9/how to handle the frames/ ig]\frames


9.  handling the Iframe

1. It is a frame or a page where extended pages are embedded
2. We cannot directly interact with frames element as it is inside another frame


There are 2 ways that we can work on locators:
1. By using frameLocator - only we can provide the locator
2. By using the frame - where we can provide the name or url of the frame

Example 1 : using the frame- name or url

const frame1=await page.frame({url:'https://ui.vision/demo/webtest/frames/frame_1.html'})
await frame1.fill("//input[@name='mytext1']","hello")


Example 2: using the locator
const inputBox=await page.frameLocator("frame[src='frame_1.html']").locator("//input[@name='mytext1']")
await inputBox.fill("Jonita")


10.handling the nested frames

If the frames are inside another frames - then we can use it

 await page.goto("https://ui.vision/demo/webtest/frames")
    const frame3=await page.frame({url:'https://ui.vision/demo/webtest/frames/frame_3.html'})
   const childFrames= await frame3.childFrames()
   await childFrames[0].locator('//div[@id="i8"]').check()





11. How to handle the webtable and paginations

1.1 Handling the web tables

Example:

 await page.goto("https://testautomationpractice.blogspot.com/")
   const table= await page.locator("#productTable")


   const col= await table.locator("thead tr th")
   console.log("number of columns",await col.count())

   //to get the rows
   const rows = await table.locator("tbody tr")
   console.log("number os rows",await rows.count())

    expect(await col.count()).toBe(4)
    expect(await rows.count()).toBe(5)


    // const matchedRow= rows.filter({
    //   has: page.locator("td"),
    //   hasText:'Product 4'

    // } )
    //await matchedRow.locator('input').check();
   await  page.waitForTimeout(4000)
await selectProduct(rows,page,'Product 1')
await selectProduct(rows,page,'Product 3')
await selectProduct(rows,page,'Product 4')


  })

  async function selectProduct(rows, page , name)
  {
    const matchedRow= rows.filter({
      has: page.locator("td"),
      hasText:name

    } )
    await matchedRow.locator('input').check();




12. Handling the date


Logic to handle the date picker

 await page.goto("https://testautomationpractice.blogspot.com/")

    //if we have option to enter the date directly/ inputting then we can use below one
// await page.fill("#datepicker","21/09/2024")
// await page.waitForTimeout(4000)

const day='23'
const month='December'
const year="2024"

await page.locator("#datepicker").click()
while(true)
  {
   const  currentmonth=await page.locator(".ui-datepicker-month").textContent()
   const currentYear=await page.locator(".ui-datepicker-year").textContent()

   if(currentmonth==month && currentYear==year)
    {
      break;

    }
    await page.locator('[title="Next"]').click()
   // await page.waitForTimeout(5000)
  }

//we need to check for the curremt monmth/ year

const dateList=await page.$$("//a[@class='ui-state-default']")

for(const dt of dateList)
  {
    if(await dt.textContent()==day)
      {
        await dt.click()
        break;
      }
  }
  await page.waitForTimeout(5000)




  })

  test.only("practising the date picker",async({page})=>
  {
    await page.goto("https://www.makemytrip.com/railways/")
    const datePickerbtn=await page.locator("#travelDate").first()
   const day='23'
   const month='November'
   const year="2024"
   await datePickerbtn.click()

   const dateText=await page.locator('//div[@class="DayPicker-Month"][1] //div[@class="DayPicker-Caption"] //div').textContent()
   console.log(dateText)

   const splitText=dateText.split(' ')
   const month1= splitText[0]
   const year1= splitText[1]
while(true)
  {
    if(month1.trim() === month && year1.trim() === year)
      {
        break;
      }
      await page.locator('[aria-label="Next Month"]').click({force:true})





13. Handle the mouse hover actions

How to mouseover
1. Store the locator whoever you want to mouse hover
2. Then with then help of that locator perform hover()

Syntax :
Locator.hover()
Example

   await page.goto("https://www.amazon.in/")
   const signInhover= await page.locator("#nav-link-accountList").first()
   await signInhover.hover()
   await  page.waitForTimeout(3000)



14. Handle the right click option

1. We can perform  right left and middle operation
Syntax:

 await button.click({button:'right'})



 await page.goto("http://swisnl.github.io/jQuery-contextMenu/demo.html")
   const button= page.locator(".context-menu-one.btn")
   await button.click({button:'right'})
   await page.waitForTimeout(3000)





15. Handle the double click

    const dblclickBtn=await page.locator("//button[text()='Copy Text']")
    await dblclickBtn.dblclick()

    const field=await page.locator("#field2")
    await expect(field).toHaveValue("Hello World!")
    await page.waitForTimeout(3000)





16. Handle the drag and drop
dragTo keyword is used

 const dragEle=await page.locator("#box3")
    const dropEle=await page.locator("#box104")
    await dragEle.dragTo(dropEle)
    await page.waitForTimeout(3000)



17. Perform mouse actions
To use any keyboard actions

Use keyboard 


await page.goto("https://gotranscript.com/text-compare")
    const textField=await page.locator('[name="text1"]')
    await textField.fill("Hellow Jonita")
    await page.keyboard.press('Meta+A')
    await page.keyboard.press('Meta+C')

    await page.keyboard.down('Tab')
    await page.keyboard.up('Tab')

    await page.keyboard.press('Meta+V')



18.dealing with uploading the files


We should use the setinputfiles(“”) - single file
Locator.setInputFiles([“”,””]). - multiple files then store it in array and upload it
uploadBtn.setInputFiles([]) - if we want to deselect  it then use the empty array
 


const uploadBtn=await page.locator("#fileInput")
await uploadBtn.setInputFiles(['tests/UploadFiles/JonitaDsouza_Resume.pdf'])
await page.waitForTimeout(2000);
await uploadBtn.setInputFiles([])
await page.waitForTimeout(4000);




19.Hooks : avoid duplicate code 
Beforeeach - executed before each individual test
After each - executed after each individual test
beforeAll - executed once before any of the test starts running
afterAll- executed once after all of the test are executed


Syntax for beforeAll and AfterAll

This will not support the page fixtures directly so we need to use the browser fixtures and create the page fixture
So declared the  page variable globally

let page;

test.beforeEach(async({browser})=>
{
   page=await browser.newPage();
   await page.goto("https://www.demoblaze.com/index.html")
   await page.locator("#login2").click()
   await page.locator("#loginusername").fill("dummy_username")
   await page.locator("#loginpassword").fill("dummypass")
   await page.locator('[onclick="logIn()"]').click()
});

test.afterEach("logout",async({})=>
{
    await page.locator("#logout2").click()
    
})



In beforeEach and afterEach we can use the page fixture - same syntax as above but we can use the page fixtures within it






20.Achieve the grouping concepts


- Grouping of the test cases under the describe block
- Set of test cases stored under the one group

example:

test.describe("group1",()=>
{
    test("test0",()=>
        {
            console.log("test--1")
        })
        
        test("test",()=>
        {
            console.log("test--2")
        })
})




21: capturing the screenshots

There are 3 ways we can capture the scereenshot

1. Current page
2. Full page screenshot
3. Particular element screenshot
4. You can also have the screenshot for all the test in ima report - in config file. Add -use: {

    /* Collect trace when retrying the failed test. See https://playwright.dev/docs/trace-viewer */
    trace: 'on-first-retry',
    headless:false,
    screenshot:'on'
  },


Example to how to capture the screenshot:
test.describe.only("handling the screenshots",()=>
  {
  test("page screenshot",async({page})=>
    {
      await page.goto("https://practice.expandtesting.com/upload")
      await page.screenshot({path:'tests/screenshots/'+Date.now()+'HomePage.png'})

    })
 test("Full page screenshot",async({page})=>
  {
    await page.goto("https://practice.expandtesting.com/upload")
      await page.screenshot({path:'tests/screenshots/'+Date.now()+'fullPage.png',fullPage:true})
      
   })
test.only("Element screenshot",async({page})=>
 {
  await page.goto("https://practice.expandtesting.com/upload")
      await page.locator("//li[text()='File Uploader']").screenshot({path:'tests/screenshots/'+Date.now()+'element.png'})
      
    
 })



22. How to record a video of the tests

In config.js we can change the setting of the video or screenshot inside the use array
We have multiple options for the video recording like when to record the video like only during the failure/ on / off

use: {
    video:'on'
  },




23.Record and playback - codegen

Execute— npx playwright codeine

Instead of copying manually we can directly - npx playwright codegen -o tests/mytest.spec.js
Here the code will be generated and stored inside the specified file



24. Trace viewver

In config we need to do some changes in the use:

use: {
    video:'on'
  },

After executing the tests - we will get the traces we can execute the command see the trace of the executed tests
Here we can check everything 




25.Tags



By giving tags- we can execute whichver tests we want to run 

Syntax

test('test login page', {tag: '@fast', }, async ({ page }) => {
   console.log("jonita")
  });
  
  test('test full report @slow', async ({ page }) => {
   console.log("Dsouza")
  });

test("test 1",{tag:'@sanity'},({})=>
{
console.log("Tests1")
})


How to run the file

npx playwright test annotations.spec.js --project=chromium --grep @sanity —grep-invert @regression



@Annotations































  	









