Hey everyone! 👋
I’ve been trying to work on myself and cut down on addictive stuff like Instagram, TikTok, and even YouTube. I didn’t want to quit YouTube completely though, because it still has tons of really useful content. The real problem? YouTube Shorts — they’re insanely addictive, and before you know it, hours have gone by.
So, with a little help from ChatGPT, I set up a way to completely remove YouTube Shorts. Here’s how you can do it too:
________________________________________
Step 1: Tampermonkey
1.  Download and install the Tampermonkey extension from here https://www.tampermonkey.net .
2.  Go to the Tampermonkey dashboard (top-right corner), click the “+” button, and paste this code:
// ==UserScript==
// @name         YouTube Shorts Terminator 2025
// @namespace    http://tampermonkey.net/
// @version      3.0
// @description  Removes all YouTube Shorts and redirects shorts URLs
// @author       ChatGPT
// @match        https://www.youtube.com/*
// @grant        none
// ==/UserScript==

(function () {
    'use strict';

    // Redirect shorts to normal video
    if (location.pathname.startsWith("/shorts/")) {
        const id = location.pathname.split("/shorts/")[1].split("?")[0];
        if (id) window.location.href = `https://www.youtube.com/watch?v=${id}`;
    }

    function isShort(element) {
        if (!element) return false;
        const aTag = element.querySelector('a[href*="/shorts/"]');
        const href = element?.href  '';
        return aTag  href.includes('/shorts/');
    }

    function removeShorts() {
        document.querySelectorAll('ytd-rich-grid-media, ytd-video-renderer, ytd-grid-video-renderer, ytd-reel-shelf-renderer')
            .forEach(el => {
                if (isShort(el)) el.remove();
            });
    }

    const observer = new MutationObserver(() => removeShorts());
    observer.observe(document.body, { childList: true, subtree: true });
    removeShorts();
})();
3.  Go back to the dashboard, click “+” again, and paste this code:
// ==UserScript==
// @name         Kill YouTube Shorts Button (Top Left, English UI)
// @namespace    http://tampermonkey.net/
// @version      6.0
// @description  Removes the "Shorts" icon from the top-left YouTube mini guide near the logo (English UI only, Edge/Desktop tested and stable on SPA navs)
// @author       You
// @match        https://www.youtube.com/*
// @grant        none
// ==/UserScript==

(function () {
    'use strict';

    function removeShortsButton() {
        const buttons = document.querySelectorAll('ytd-mini-guide-entry-renderer');

        buttons.forEach(btn => {
            const label = btn.getAttribute('aria-label')?.toLowerCase();
            const text = btn.innerText?.trim().toLowerCase();
            const link = btn.querySelector('a')?.getAttribute('href');

            if (
                (text === 'shorts') 
                (label && label.includes('shorts')) 
                (link && link.startsWith('/shorts'))
            ) {
                btn.style.display = 'none';
            }
        });
    }

    // Run initially
    removeShortsButton();

    // Observe for YouTube's dynamic page behavior
    const observer = new MutationObserver(() => {
        removeShortsButton();
    });

    observer.observe(document.body, {
        childList: true,
        subtree: true
    });
})();
4.  Go to “Utilities” and click “Check for Userscript Updates”.
________________________________________
Step 2: uBlock Origin
1.  Download and install the uBlock extension from here https://ublockorigin.com .
2.  Click on the uBlock extension, then click “Settings” in the bottom-right corner.
3.  Copy and paste the following code into uBlock’s “My Filters”:
! ====== Remove Shorts button in the left mini guide (sidebar) ======
www.youtube.com##ytd-mini-guide-entry-renderer:has-text(Shorts)
www.youtube.com##ytd-guide-entry-renderer:has-text(Shorts)

! ====== Remove Shorts tab in the top navigation bar ======
www.youtube.com##tp-yt-paper-tab:has(a[href^="/shorts"])
www.youtube.com##a[title="Shorts"]
www.youtube.com##a[href^="/shorts"]

! ====== Remove Shorts video shelves on homepage and elsewhere ======
www.youtube.com##ytd-rich-shelf-renderer:has-text(Shorts)
www.youtube.com##ytd-rich-item-renderer:has(a[href^="/shorts"])
www.youtube.com##ytd-rich-grid-media:has(a[href^="/shorts"])

! ====== Remove Shorts thumbnails anywhere on site ======
www.youtube.com##ytd-thumbnail a[href^="/shorts"]

! ====== Remove Shorts from subscriptions and other feeds ======
www.youtube.com##ytd-rich-shelf-renderer:has-text(Shorts)
www.youtube.com##ytd-video-renderer:has(a[href^="/shorts"])

www.youtube.com##ytd-rich-shelf-renderer:has-text(Breaking news)
www.youtube.com##ytd-rich-grid-media:has-text(Breaking news)
4.  In the top-left corner, click “Apply Changes”.
5.  Go to YouTube and refresh the page! 🎉
________________________________________
After this, YouTube Shorts should be completely gone — no sidebar buttons, no top tabs, no thumbnails, no video shelves. You can finally focus on the content that actually matters. ✅
