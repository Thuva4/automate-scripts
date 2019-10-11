This script will work in browser. This will help you scrape all the file(directly send through telegram) from particular channel or chat.

```
let preCount=0
let sameCount=0
let links = []
let scrollToTop = () => {
    console.log(preCount)
    console.log(sameCount)
	let myDiv = document.querySelector('.im_history_message_wrap');
	myDiv.scrollIntoView();
	let divs = document.querySelectorAll('.im_message_text');
	if (preCount == divs.length) {
        sameCount+=1;
    } else{
        sameCount=0;
        preCount = divs.length;
    }
    let timeOut;
    if(sameCount!=5) {
        timeOut = setTimeout(scrollToTop, 3000);
    } else {
        clearTimeout(timeOut);
        timeOut=0;
        console.log(preCount)
        let messagesDivs = document.querySelectorAll('.im_message_document_actions > a.nocopy')
        for (const message of messagesDivs) {
           download(message)
        }
        console.log("Finished!")
    }
};

let download = async(element) => {
    await message.click()
    await sleep(10000);
}

function sleep(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

scrollToTop()

```
