# Adding Github Labels En Masse
If you want to add custom labels to your repo quickly without using the CLI, this is the way to do it. This template is prefilled with the default labels that are created for new repos within Obsidian-TTRPG-Community, but you can change them as you will.

## The Code
```js
const labels = [
    {
        "name": "Debugging Charm",
        "description": "[Bug] The caster attempts to diagnose and resolve issues with the targeted object or system.",
        "color": "d73a4a"
    },
    {
        "name": "Mimic!",
        "description": "[Duplicate] Mimic is disguising itself as an existing issue or pull request.",
        "color": "cfd3d7"
    },
    {
        "name": "Conjure Enhancement",
        "description": "[Feature] The caster has conjured forth a new feature or request to be added to the stronghold.",
        "color": "a2eeef"
    },
    {
        "name": "Voluntary Enlistment",
        "description": "[Good First Issue] This issue is well-suited for new recruits who are eager to join the stronghold.",
        "color": "7057ff"
    },
    {
        "name": "Call Reinforcements",
        "description": "[Help Wanted] A banner is slammed into the ground, summoning allies to aid in the issue.",
        "color": "008672"
    },
    {
        "name": "Misguided Path",
        "description": "[Invalid] The issue or pull request has been filed is in the wrong place, as if the target is lost.",
        "color": "e4e669"
    },
    {
        "name": "Compel Secrets",
        "description": "[Question] The target is compelled to provide additional information upon questioning.",
        "color": "d876e3"
    },
    {
        "name": "Nat 1",
        "description": "[Wontfix] The target rolled a Nat 1, and failed their talk check. Their request has been denied.",
        "color": "FFFFFF"
    },
    {
        "name": "Nat 20",
        "description": "[Work In Progress] The target rolled Nat 20 and passed their talk check. Their request is accepted.",
        "color": "0E8A16"
    },
    {
        "name": "Summon Scribe",
        "description": "[Documentation] An expert in writing is summoned to make needed improvements to the scrolls.",
        "color": "0075ca"
    }
];

// Function to update an existing label
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
