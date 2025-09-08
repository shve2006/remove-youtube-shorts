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
                (text === 'shorts') ||
                (label && label.includes('shorts')) ||
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
