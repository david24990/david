<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Confession</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
    body {
        background: linear-gradient(135deg, #f8b6d2 0%, #b6e0fe 100%);
        min-height: 100vh;
        margin: 0;
        font-family: 'Segoe UI', Arial, sans-serif;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: relative;
        padding: 10px;
        box-sizing: border-box;
    }
    .side-img {
        position: absolute;
        top: 50%;
        transform: translateY(-50%);
        width: 20vw;
        max-width: 150px;
        height: auto;
        z-index: 1;
        opacity: 0;
        transition: opacity 1.5s;
    }
    .side-img.show {
        opacity: 1;
    }
    .left-img {
        left: 10px;
    }
    .right-img {
        right: 10px;
    }
    .confession-box {
        background: rgba(255,255,255,0.85);
        border-radius: 20px;
        box-shadow: 0 8px 32px rgba(0,0,0,0.15);
        padding: 20px;
        text-align: center;
        position: relative;
        z-index: 2;
        width: 100%;
        max-width: 500px;
        box-sizing: border-box;
    }
    h1 {
        color: #e75480;
        margin-bottom: 10px;
        font-size: 1.8em;
    }
    p {
        font-size: 1.2em;
        color: #444;
        margin-bottom: 20px;
    }
    .btn {
        padding: 12px 30px;
        font-size: 1em;
        border: none;
        border-radius: 25px;
        margin: 8px;
        cursor: pointer;
        transition: background 0.2s, transform 0.2s;
        position: relative;
    }
    #yesBtn {
        background: #e75480;
        color: #fff;
    }
    #yesBtn:hover {
        background: #d13b6f;
        transform: scale(1.08);
    }
    #noBtn {
        background: #fff;
        color: #e75480;
        border: 2px solid #e75480;
    }
    #noBtn:hover {
        background: #ffe3ed;
        transform: scale(1.08);
    }
    #message {
        font-size: 1.3em;
        color: #e75480;
        margin-top: 20px;
        opacity: 0;
        transition: opacity 1s;
    }
    #confessionVideo {
        display: none;
        margin: 20px auto 0 auto;
        border-radius: 16px;
        box-shadow: 0 4px 16px rgba(0,0,0,0.12);
        width: 100%;
        max-width: 100%;
        height: auto;
        background: #000;
    }
    /* Mobile adjustments */
    @media (max-width: 600px) {
        .side-img {
            display: none;
        }
        h1 {
            font-size: 1.5em;
        }
        p {
            font-size: 1em;
        }
        .btn {
            width: 80%;
            max-width: 250px;
        }
    }
</style>
</head>
<body>
    <img src="https://i.pinimg.com/736x/d7/1a/5c/d71a5caddaadb53a46ba6b1f1349274f.jpg" class="side-img left-img" alt="Left Image">
    <div class="confession-box">
        <h1>💌 hello!</h1>
        <p>Would you make me the happiest person and be my special someone?</p>
        <button class="btn" id="yesBtn">Yes</button>
        <button class="btn" id="noBtn">No</button>
        <div id="message">You said YES! 💖</div>
        <video id="confessionVideo" autoplay playsinline>
            <source src="ssstik.io_@scytheivx_1755092058187.mp4" type="video/mp4">
        </video>
    </div>
    <img src="https://i.pinimg.com/736x/1c/5e/88/1c5e88ae5848ce1f7a4bce03c2eb763b.jpg" class="side-img right-img" alt="Right Image">

<script>
    const noBtn = document.getElementById('noBtn');
    const yesBtn = document.getElementById('yesBtn');
    const message = document.getElementById('message');
    const video = document.getElementById('confessionVideo');
    const box = document.querySelector('.confession-box');

    function moveNoBtn() {
        const boxRect = box.getBoundingClientRect();
        const btnWidth = noBtn.offsetWidth;
        const btnHeight = noBtn.offsetHeight;
        const maxLeft = boxRect.width - btnWidth - 20;
        const maxTop = boxRect.height - btnHeight - 20;
        const left = Math.random() * maxLeft;
        const top = Math.random() * maxTop;
        noBtn.style.position = 'absolute';
        noBtn.style.left = left + 'px';
        noBtn.style.top = top + 'px';
    }

    noBtn.addEventListener('mouseover', moveNoBtn);
    noBtn.addEventListener('click', moveNoBtn);

    yesBtn.addEventListener('click', function() {
        message.style.opacity = 1;
        video.style.display = 'block';
        video.play();
        document.querySelectorAll('.side-img').forEach(img => img.classList.add('show'));
    });

    video.addEventListener('pause', function() {
        video.play();
    });
    video.addEventListener('ended', function() {
        video.currentTime = 0;
        video.play();
    });
</script>
</body>
</html>

