# Adding Github Labels En Masse
If you want to add custom labels to your repo quickly without using the CLI, this is the way to do it. This template is prefilled with the default labels that are created for new repos within Obsidian-TTRPG-Community, but you can change them as you will.

## The Code
```js
/*
Purpose: Import settings for GitHub Labels.
(c) James Perrin, MIT License, https://www.countrydawgg.com, | @jamesperrin
Importing Instructions:
1. Update the labels JSON object.
2. Open a web browser.
3. Navigate to the desired GitHub repository.
4. Navigate to Issues tab.
5. Navigate to Labels link.
6. Open the web browswer's Developer Tools
7. Navigate to the Console window.
8. Copy and Paste the below code snippets into the Console window.
Please visit the below link to download the export JavaScript script.
github-labels-export.js - https://gist.github.com/jamesperrin/c2bf6d32fbb8142682f6107e561b664d
*/

const labels = [
    {
        "name": "Nat 20",
        "description": "The target rolled a Nat 20, and succeeded their talk check. Their request has been accepted.",
        "color": "0e8a16"
    },
    {
        "name": "Call Reinforcements",
        "description": "A banner is slammed into the ground, summoning allies to aid in the issue.",
        "color": "008672"
    },
    {
        "name": "Conjure Enhancement",
        "description": "The caster has conjured forth a new feature or request to be added to the stronghold.",
        "color": "a2eeef"
    },
    {
        "name": "Debugging Charm",
        "description": "The caster attempts to diagnose and resolve issues with the targeted object or system.",
        "color": "d73a4a"
    },
    {
        "name": "Inquire Follower",
        "description": "The target is compelled to provide additional information upon questioning.",
        "color": "d876e3"
    },
    {
        "name": "Mimic!",
        "description": "A creature has infiltrated the stronghold, disguising itself as an existing issue or pull request.",
        "color": "cfd3d7"
    },
    {
        "name": "Misguided Path",
        "description": "The issue or pull request has been filed in the wrong stronghold, as if the target is lost.",
        "color": "e4e669"
    },
    {
        "name": "Nat 1",
        "description": "The target rolled a Nat 1, and failed their talk check. Their request has been denied.",
        "color": "ffffff"
    },
    {
        "name": "Summon Scribe",
        "description": "An expert in writing and art is summoned to make needed improvements and additions to the scrolls.",
        "color": "0075ca"
    },
    {
        "name": "Voluntary Enlistment",
        "description": "This issue is well-suited for new recruits who are eager to join the stronghold.",
        "color": "7057ff"
    }
];

// Function to update an existing label
function updateLabel(label) {
    let flag = false;

    [].slice.call(document.querySelectorAll('.labels-list-item')).map((element) => {
        if (element.querySelector('.label-link').textContent.trim() === label.name) {
            flag = true;
            element.querySelector('.js-edit-label').click();
            element.querySelector('.js-new-label-name-input').value = label.name;
            element.querySelector('.js-new-label-description-input').value = label.description;
            element.querySelector('.js-new-label-color-input').value = `#${label.color}`;
            element.querySelector('.js-edit-label-cancel ~ .btn-primary').click();
        }
    });

    return flag;
}

// Function to add a new label
function addNewLabel(label) {
    document.querySelector('.js-new-label-name-input').value = label.name;
    document.querySelector('.js-new-label-description-input').value = label.description;
    document.querySelector('.js-new-label-color-input').value = `#${label.color}`;
    document.querySelector('.js-details-target ~ .btn-primary').disabled = false;
    document.querySelector('.js-details-target ~ .btn-primary').click();
}

// Function to add a new label
function addLabel(label) {
    if (!updateLabel(label)) {
        addNewLabel(label);
    }
}

labels.map((label) => {
    addLabel(label);
});
```
