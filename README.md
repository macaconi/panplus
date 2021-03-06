Panopto Plus

#### Purpose of this project
To create a chrome extension to improve the webcasting experience for panopto. It will serve a few purposes:

1. Improve the user interface of the webcast page. 

2. Add transcript & subtitles. The idea is to add this into the user interface as subtitles and as a transcript section on the page that users can click and the video will skip to that part like in Youtube (example video which has transcripts / subtitles https://www.youtube.com/watch?v=xa-4IAR_9Yw). This should be implemented in the non-fullscreen and full-screen version.

3. Remove / Speed up sections where the prof is not speaking in the webcast (inspired by https://www.youtube.com/watch?v=DQ8orIurGxw). This will shorten the duration of the webcast and improve UX.

### Development Instructions
1. Clone this git repository on your computer.
2. Launch Google Chrome & put in "chrome://extensions" in the URL.
3. Switch on Developer mode (top right corner).
4. Select "Load Unpacked" and select the "PanoptoPlus" folder.
5. The extension is loaded. Whenever you need to modify and test code, load the extension like in step 4 and reload the page.

### Deployment Instructions
The extension can be used as is by following the development instructions. However, the production distribution is not ready yet.

### Todo List
__User Interface__
  * __Double video webcast__
    * App specific sidebar [DONE]
    * Minimized carousel size [DONE]
    * Persistent settings
    * Subtitles toggle option
  * __Single video webcast__
    * App specific sidebar
    * Minimize carousel size
    * Consistent UI with Double video webcast
  * __Mobile: Double video webcast__
  * __Mobile: Single video webcast__

__Transcripts__
* Extraction of transcripts [DONE]
* Separation of interface & implementation [Separate subtitle source]
* Conversion of transcripts to WebVTT tracks for subtitling [DONE]
* Conversion of transcripts to DOM in sidebar³

__Silence Trimming__
* Implementation⁴

__Complete Conversion to ES6__
* Implementation

__Webpack for deployment__
* Implementation

---
³Will need to manage hundreds of transcript rows. Use something that can handle that: https://github.com/triceam/MegaList. Each transcript row also needs to be clickable and seek video to position.  
⁴ https://github.com/otalk/hark    


### Interesting Keep In View (KIV) Concepts
* User submitted edits to subtitles 
  * To ensure integrity, submitters will have to login using NUS account to verify themselves with our server (OAuth2, https://wiki.nus.edu.sg/pages/viewpage.action?pageId=235638755).
  * Voting System with regards to which subtitle to prioritise
  * Symmetric Key Encryption of subtitles using the ID of the webcast as the key: ensures privacy of the subtitles is not compromised even if the server is compromised.
* Webcast download KIV
  * Downloaded webcast is sped-up, trimmed appropriately and subtitled. First, extract video. Then use ffmpeg to trim, speed up and the subtitle.
  * ffmpeg: https://github.com/Kagami/ffmpeg.js/
  * Speed: https://davidwalsh.name/video-speed
  * Slicing: https://superuser.com/questions/681885/how-can-i-remove-multiple-segments-from-a-video-using-ffmpeg
  * https://stackoverflow.com/questions/48268720/ffmpeg-commands-in-javascript
  * Burning the subs in (if configured by user): https://stackoverflow.com/questions/8672809/use-ffmpeg-to-add-text-subtitles
  * https://stackoverflow.com/questions/52543728/ffmpeg-adding-and-removing-subtitles-without-changing-the-video
* Other non-critical features e.g. export notes

### Known Bugs
#### Most Likely fixed, but keep a look-out for
* Race condition when loading page, videos fail to load due to replacement of speed flyouts

#### Unfixed
* No existing known bugs

### Test URLs
a) Double videos webcasts:
https://nuscast.ap.panopto.com/Panopto/Pages/Viewer.aspx?id=e8d44d91-652d-4e41-8482-a9d6003357fe

b) Single video webcasts
https://nuscast.ap.panopto.com/Panopto/Pages/Viewer.aspx?id=626cd545-dfb4-4a8a-ae05-a9d8007dd2f8


### Bibliography
https://stackoverflow.com/questions/2844565/is-there-a-javascript-jquery-dom-change-listener
https://stackoverflow.com/questions/35023051/making-javascript-function-inaccessible-from-console
https://stackoverflow.com/questions/9515704/insert-code-into-the-page-context-using-a-content-script
https://www.phpied.com/3-ways-to-define-a-javascript-class/
https://stackoverflow.com/questions/7694501/class-vs-static-method-in-javascript
https://stackoverflow.com/questions/1279957/how-to-move-an-element-into-another-element?rq=1
https://stackoverflow.com/questions/15873904/adding-complex-html-using-a-chrome-content-script
https://medium.freecodecamp.org/how-to-create-a-chrome-extension-part-1-ad2a3a77541