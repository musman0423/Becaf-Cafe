<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>DOS WordPad</title>

<style>
    * {
        box-sizing: border-box;
    }

    body {
        margin: 0;
        background: #000;
        color: #00ff00;
        font-family: "Courier New", monospace;
        min-height: 100vh;
    }

    .dos-screen {
        width: 100%;
        min-height: 100vh;
        padding: 15px;
        background: #000;
    }

    .title {
        text-align: center;
        color: #00ff00;
        font-size: 30px;
        font-weight: bold;
        margin-bottom: 15px;
        text-shadow: 0 0 8px #00ff00;
    }

    .top-line {
        border-top: 1px solid #00ff00;
        border-bottom: 1px solid #00ff00;
        padding: 8px;
        text-align: center;
        margin-bottom: 15px;
    }

    button {
        background: #000;
        color: #00ff00;
        border: 1px solid #00ff00;
        padding: 10px 16px;
        margin: 4px;
        font-family: "Courier New", monospace;
        font-size: 15px;
        cursor: pointer;
    }

    button:hover {
        background: #00ff00;
        color: #000;
    }

    .main {
        display: flex;
        gap: 15px;
        align-items: flex-start;
    }

    /* DIRECTORY */
    .directory {
        width: 300px;
        min-height: 600px;
        border: 1px solid #00ff00;
        padding: 10px;
        flex-shrink: 0;
    }

    .directory h2 {
        font-size: 18px;
        text-align: center;
        border-bottom: 1px solid #00ff00;
        padding-bottom: 8px;
        margin-top: 0;
    }

    .file-list {
        max-height: 500px;
        overflow-y: auto;
    }

    .file-item {
        border-bottom: 1px dotted #00ff00;
        padding: 10px 4px;
        cursor: pointer;
    }

    .file-item:hover {
        background: #003300;
    }

    .file-name {
        font-weight: bold;
    }

    .file-date {
        font-size: 11px;
        margin-top: 4px;
    }

    .file-actions {
        margin-top: 6px;
    }

    .file-actions button {
        font-size: 11px;
        padding: 4px 7px;
    }

    /* EDITOR */
    .editor-area {
        flex: 1;
        min-width: 0;
    }

    .toolbar {
        border: 1px solid #00ff00;
        padding: 8px;
        margin-bottom: 10px;
    }

    .filename {
        width: 250px;
        background: #000;
        color: #00ff00;
        border: 1px solid #00ff00;
        padding: 9px;
        font-family: "Courier New", monospace;
    }

    .status {
        margin: 8px 0;
        font-size: 13px;
    }

    /* A4 PAGE */
    .page-container {
        width: 100%;
        display: flex;
        justify-content: center;
        overflow-x: auto;
        padding: 10px;
    }

    .a4-page {
        background: #fff;
        color: #000;
        width: 794px;
        min-height: 1123px;
        padding: 65px;
        box-shadow: 0 0 15px #00ff00;
        outline: none;
        font-family: Arial, sans-serif;
        font-size: 16px;
        line-height: 1.5;
        white-space: pre-wrap;
    }

    .a4-page:focus {
        box-shadow: 0 0 25px #00ff00;
    }

    .bottom-bar {
        border-top: 1px solid #00ff00;
        margin-top: 15px;
        padding-top: 10px;
        text-align: center;
        font-size: 12px;
    }

    .empty {
        text-align: center;
        margin-top: 30px;
        font-size: 13px;
    }

    @media (max-width: 900px) {
        .main {
            flex-direction: column;
        }

        .directory {
            width: 100%;
            min-height: auto;
        }

        .file-list {
            max-height: 250px;
        }

        .a4-page {
            width: 794px;
        }
    }
</style>
</head>

<body>

<div class="dos-screen">

    <div class="title">
        DOS WORDPAD
    </div>

    <div class="top-line">
        C:\DOS\WORDPAD&gt;
    </div>

    <div style="text-align:center;">
        <button onclick="newFile()">[ NEW WORD FILE ]</button>
        <button onclick="openLastFile()">[ OPEN LAST SAVE FILE ]</button>
        <button onclick="showDirectory()">[ DIRECTORY ]</button>
    </div>

    <div class="main">

        <!-- DIRECTORY -->
        <div class="directory">

            <h2>
                C:\DOS\WORDPAD\FILES
            </h2>

            <div id="fileList" class="file-list">
            </div>

        </div>

        <!-- EDITOR -->
        <div class="editor-area">

            <div class="toolbar">

                FILE NAME:

                <input
                    type="text"
                    id="fileName"
                    class="filename"
                    placeholder="Enter file name"
                >

                <br>

                <button onclick="saveFile()">
                    [ SAVE FILE ]
                </button>

                <button onclick="clearEditor()">
                    [ CLEAR ]
                </button>

            </div>

            <div class="status" id="status">
                STATUS: READY
            </div>

            <div class="page-container">

                <div
                    id="editor"
                    class="a4-page"
                    contenteditable="true"
                    spellcheck="true"
                ></div>

            </div>

        </div>

    </div>

    <div class="bottom-bar">
        DOS WORDPAD &nbsp; | &nbsp;
        LOCAL FILE DIRECTORY &nbsp; | &nbsp;
        READY
    </div>

</div>


<script>

    const STORAGE_KEY = "DOS_WORDPAD_FILES";

    let currentFileId = null;


    // GET ALL SAVED FILES
    function getFiles() {

        const files =
            localStorage.getItem(STORAGE_KEY);

        return files ? JSON.parse(files) : [];
    }


    // SAVE ALL FILES
    function setFiles(files) {

        localStorage.setItem(
            STORAGE_KEY,
            JSON.stringify(files)
        );

    }


    // DISPLAY DIRECTORY
    function showDirectory() {

        renderDirectory();

        setStatus(
            "DIRECTORY: FILE LIST UPDATED"
        );

    }


    // RENDER FILE DIRECTORY
    function renderDirectory() {

        const fileList =
            document.getElementById("fileList");

        const files = getFiles();

        fileList.innerHTML = "";

        if (files.length === 0) {

            fileList.innerHTML =
                '<div class="empty">NO FILES FOUND</div>';

            return;
        }


        files.sort(
            (a, b) =>
                new Date(b.date) -
                new Date(a.date)
        );


        files.forEach(file => {

            const item =
                document.createElement("div");

            item.className = "file-item";


            const name =
                document.createElement("div");

            name.className = "file-name";

            name.textContent =
                ">" + file.name;


            const date =
                document.createElement("div");

            date.className = "file-date";

            date.textContent =
                file.date;


            const actions =
                document.createElement("div");

            actions.className =
                "file-actions";


            const openButton =
                document.createElement("button");

            openButton.textContent =
                "OPEN";

            openButton.onclick = function(e) {

                e.stopPropagation();

                openFile(file.id);

            };


            const deleteButton =
                document.createElement("button");

            deleteButton.textContent =
                "DELETE";

            deleteButton.onclick =
                function(e) {

                    e.stopPropagation();

                    deleteFile(file.id);

                };


            actions.appendChild(openButton);

            actions.appendChild(deleteButton);


            item.appendChild(name);

            item.appendChild(date);

            item.appendChild(actions);


            item.onclick =
                function() {

                    openFile(file.id);

                };


            fileList.appendChild(item);

        });

    }


    // CREATE NEW FILE
    function newFile() {

        currentFileId = null;

        document.getElementById(
            "fileName"
        ).value = "";

        document.getElementById(
            "editor"
        ).innerHTML = "";

        document.getElementById(
            "fileName"
        ).focus();

        setStatus(
            "NEW FILE: READY FOR WRITING"
        );

    }


    // SAVE FILE
    function saveFile() {

        const fileName =
            document.getElementById(
                "fileName"
            ).value.trim();

        const content =
            document.getElementById(
                "editor"
            ).innerHTML;


        if (!fileName) {

            alert(
                "Please enter a file name."
            );

            document.getElementById(
                "fileName"
            ).focus();

            return;
        }


        if (
            !document.getElementById(
                "editor"
            ).innerText.trim()
        ) {

            alert(
                "Please write something before saving."
            );

            return;
        }


        const files = getFiles();

        const now =
            new Date().toLocaleString();


        // UPDATE EXISTING FILE
        if (currentFileId) {

            const index =
                files.findIndex(
                    f =>
                        f.id === currentFileId
                );


            if (index !== -1) {

                files[index].name =
                    fileName;

                files[index].content =
                    content;

                files[index].date =
                    now;

            }

        }

        // CREATE NEW FILE
        else {

            const newFileObject = {

                id:
                    Date.now().toString(),

                name:
                    fileName,

                content:
                    content,

                date:
                    now

            };


            files.push(
                newFileObject
            );

            currentFileId =
                newFileObject.id;

        }


        setFiles(files);

        renderDirectory();

        setStatus(
            "FILE SAVED: " + fileName
        );

    }


    // OPEN FILE
    function openFile(id) {

        const files =
            getFiles();

        const file =
            files.find(
                f => f.id === id
            );


        if (!file) {

            alert(
                "File not found."
            );

            return;
        }


        currentFileId =
            file.id;


        document.getElementById(
            "fileName"
        ).value =
            file.name;


        document.getElementById(
            "editor"
        ).innerHTML =
            file.content;


        setStatus(
            "FILE OPENED: " + file.name
        );

    }


    // OPEN LAST SAVED FILE
    function openLastFile() {

        const files =
            getFiles();


        if (files.length === 0) {

            alert(
                "No saved files found."
            );

            return;
        }


        files.sort(
            (a, b) =>
                new Date(b.date) -
                new Date(a.date)
        );


        openFile(
            files[0].id
        );

    }


    // DELETE FILE
    function deleteFile(id) {

        const files =
            getFiles();

        const file =
            files.find(
                f => f.id === id
            );


        if (!file) return;


        const confirmDelete =
            confirm(
                "Delete file \"" +
                file.name +
                "\"?"
            );


        if (!confirmDelete) return;


        const remaining =
            files.filter(
                f => f.id !== id
            );


        setFiles(
            remaining
        );


        if (currentFileId === id) {

            newFile();

        }


        renderDirectory();

        setStatus(
            "FILE DELETED: " +
            file.name
        );

    }


    // CLEAR EDITOR
    function clearEditor() {

        const confirmClear =
            confirm(
                "Clear the current document?"
            );


        if (!confirmClear) return;


        document.getElementById(
            "editor"
        ).innerHTML = "";


        setStatus(
            "EDITOR CLEARED"
        );

    }


    // STATUS MESSAGE
    function setStatus(message) {

        document.getElementById(
            "status"
        ).textContent =
            "STATUS: " + message;

    }


    // INITIAL DIRECTORY LOAD
    renderDirectory();

</script>

</body>
</html>