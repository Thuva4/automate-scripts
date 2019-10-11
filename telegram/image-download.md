This script will work in browser. This will help you scrape all the image messages from particular channel or chat. 

```
let preCount=0
let sameCount=0
let scrollToTop = () => {
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
        let messagesDivs = document.querySelectorAll('.im_message_media > div >div > a.im_message_photo_thumb')
        for (const message of messagesDivs) {
            message.click();
            document.querySelectorAll('.media_modal_bottom_actions > a.media_modal_action_btn')[0].click()
            document.querySelectorAll('.modal_next_wrap')[0].click()
        }
        console.log("Finished!")
    }
};

scrollToTop()
//wait for Finished!

```