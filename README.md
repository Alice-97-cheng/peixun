<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GemDesign - 视频课件</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'PingFang SC', 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #f5f7fa 0%, #e4e8f0 100%);
            color: #333;
            line-height: 1.6;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding: 20px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }
        
        .logo {
            display: flex;
            align-items: center;
        }
        
        .logo-icon {
            width: 48px;
            height: 48px;
            background: linear-gradient(135deg, #3C8EFF 0%, #2670E8 100%);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 15px;
            color: white;
            font-size: 20px;
            font-weight: bold;
        }
        
        .logo h1 {
            font-size: 28px;
            font-weight: 700;
            background: linear-gradient(135deg, #333 0%, #3C8EFF 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
            color: #666;
            font-weight: 500;
        }
        
        .video-container {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .player-section {
            flex: 1;
            min-width: 300px;
        }
        
        .video-player {
            background-color: #000;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
            margin-bottom: 20px;
            position: relative;
        }
        
        .video-player video {
            width: 100%;
            display: block;
            border-radius: 12px 12px 0 0;
        }
        
        .player-controls {
            background: linear-gradient(to bottom, #1a1a1a, #2a2a2a);
            padding: 15px 20px;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }
        
        .progress-container {
            width: 100%;
            height: 6px;
            background-color: #444;
            border-radius: 3px;
            cursor: pointer;
            position: relative;
            transition: height 0.2s;
        }
        
        .progress-container:hover {
            height: 8px;
        }
        
        .progress-bar {
            height: 100%;
            background: linear-gradient(90deg, #3C8EFF, #4CAF50);
            border-radius: 3px;
            width: 0%;
            position: relative;
            transition: all 0.2s;
        }
        
        .progress-bar::after {
            content: '';
            position: absolute;
            right: -6px;
            top: 50%;
            transform: translateY(-50%);
            width: 12px;
            height: 12px;
            background: white;
            border-radius: 50%;
            opacity: 0;
            transition: opacity 0.2s;
        }
        
        .progress-container:hover .progress-bar::after {
            opacity: 1;
        }
        
        .control-buttons {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .left-controls, .right-controls {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        
        .control-btn {
            background: none;
            border: none;
            color: #fff;
            cursor: pointer;
            font-size: 18px;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s;
            padding: 5px;
            border-radius: 5px;
        }
        
        .control-btn:hover {
            color: #3C8EFF;
            background: rgba(255, 255, 255, 0.1);
        }
        
        .time-display {
            color: #fff;
            font-size: 14px;
            font-weight: 500;
        }
        
        .volume-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .volume-slider {
            width: 80px;
            height: 4px;
            background-color: #444;
            border-radius: 2px;
            position: relative;
            cursor: pointer;
            transition: height 0.2s;
        }
        
        .volume-slider:hover {
            height: 6px;
        }
        
        .volume-level {
            height: 100%;
            background: linear-gradient(90deg, #3C8EFF, #4CAF50);
            border-radius: 2px;
            width: 80%;
        }
        
        .video-info {
            padding: 25px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }
        
        .video-info h2 {
            font-size: 24px;
            margin-bottom: 12px;
            color: #333;
            font-weight: 600;
        }
        
        .video-info p {
            color: #666;
            font-size: 15px;
            margin-bottom: 20px;
            line-height: 1.7;
        }
        
        .video-meta {
            display: flex;
            gap: 20px;
            font-size: 14px;
            color: #888;
        }
        
        .video-meta span {
            display: flex;
            align-items: center;
            gap: 6px;
        }
        
        .playlist-section {
            flex: 0 0 320px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            overflow: hidden;
        }
        
        .playlist-header {
            padding: 20px;
            background: linear-gradient(135deg, #3C8EFF 0%, #2670E8 100%);
            color: white;
            font-weight: 600;
            font-size: 18px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .playlist {
            max-height: 500px;
            overflow-y: auto;
            padding: 10px;
        }
        
        .playlist-item {
            display: flex;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 8px;
            cursor: pointer;
            transition: all 0.3s ease;
            border: 1px solid transparent;
        }
        
        .playlist-item:hover {
            background: #f8f9fa;
            transform: translateX(5px);
            border-color: #e9ecef;
        }
        
        .playlist-item.active {
            background: linear-gradient(135deg, #e6f2ff 0%, #d4e7ff 100%);
            border-left: 4px solid #3C8EFF;
            box-shadow: 0 2px 8px rgba(60, 142, 255, 0.2);
        }
        
        .playlist-thumbnail {
            width: 80px;
            height: 60px;
            background: #eee;
            border-radius: 6px;
            margin-right: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #999;
            font-size: 12px;
            overflow: hidden;
            position: relative;
        }
        
        .playlist-thumbnail::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.1);
        }
        
        .playlist-thumbnail i {
            z-index: 1;
        }
        
        .playlist-info {
            flex: 1;
        }
        
        .playlist-title {
            font-weight: 600;
            margin-bottom: 5px;
            font-size: 14px;
            color: #333;
        }
        
        .playlist-duration {
            font-size: 12px;
            color: #888;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .footer {
            margin-top: 40px;
            text-align: center;
            padding: 25px;
            color: #666;
            font-size: 14px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
        }
        
        .footer p {
            margin-bottom: 8px;
        }
        
        .feature-highlights {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }
        
        .feature-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
            text-align: center;
            transition: transform 0.3s ease;
        }
        
        .feature-card:hover {
            transform: translateY(-5px);
        }
        
        .feature-icon {
            font-size: 32px;
            color: #3C8EFF;
            margin-bottom: 15px;
        }
        
        .feature-card h3 {
            margin-bottom: 10px;
            color: #333;
        }
        
        .feature-card p {
            color: #666;
            font-size: 14px;
        }
        
        @media (max-width: 768px) {
            .video-container {
                flex-direction: column;
            }
            
            .playlist-section {
                flex: 1;
                width: 100%;
            }
            
            .header {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
            
            .feature-highlights {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header class="header">
            <div class="logo">
                <div class="logo-icon">G</div>
                <h1>GemDesign 视频课件中心</h1>
            </div>
            <div class="user-info">
                <i class="fas fa-user-circle fa-lg"></i>
                <span>欢迎学习</span>
            </div>
        </header>
        
        <main>
            <div class="video-container">
                <section class="player-section">
                    <div class="video-player">
                        <video id="mainVideo" poster="https://images.unsplash.com/photo-1611162617474-5b21e879e113?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80">
                            <!-- 请将视频源替换为您的实际视频路径 -->
                            <source src="课件一.mp4" type="video/mp4">
                            您的浏览器不支持 HTML5 视频播放。
                        </video>
                        <div class="player-controls">
                            <div class="progress-container" id="progressContainer">
                                <div class="progress-bar" id="progressBar"></div>
                            </div>
                            <div class="control-buttons">
                                <div class="left-controls">
                                    <button class="control-btn" id="playPauseBtn">
                                        <i class="fas fa-play"></i>
                                    </button>
                                    <div class="time-display">
                                        <span id="currentTime">0:00</span> / <span id="duration">0:00</span>
                                    </div>
                                </div>
                                <div class="right-controls">
                                    <div class="volume-container">
                                        <button class="control-btn" id="volumeBtn">
                                            <i class="fas fa-volume-up"></i>
                                        </button>
                                        <div class="volume-slider" id="volumeSlider">
                                            <div class="volume-level" id="volumeLevel"></div>
                                        </div>
                                    </div>
                                    <button class="control-btn" id="fullscreenBtn">
                                        <i class="fas fa-expand"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="video-info">
                        <h2>课件一：GemDesign 入门教程</h2>
                        <p>本视频将详细介绍 GemDesign 平台的核心功能和操作流程。从界面布局到工具使用，从基础操作到高级技巧，帮助您快速掌握这一强大的设计工具。无论您是设计新手还是资深设计师，都能从中获得实用的知识和技能。</p>
                        <div class="video-meta">
                            <span><i class="far fa-calendar"></i> 2023年10月15日</span>
                            <span><i class="far fa-eye"></i> 1,245 次观看</span>
                            <span><i class="far fa-clock"></i> 15:30</span>
                        </div>
                    </div>
                    
                    <div class="feature-highlights">
                        <div class="feature-card">
                            <div class="feature-icon">
                                <i class="fas fa-play-circle"></i>
                            </div>
                            <h3>高清播放</h3>
                            <p>支持高清视频播放，提供流畅的观看体验</p>
                        </div>
                        <div class="feature-card">
                            <div class="feature-icon">
                                <i class="fas fa-keyboard"></i>
                            </div>
                            <h3>快捷键支持</h3>
                            <p>空格播放/暂停，方向键控制进度和音量</p>
                        </div>
                        <div class="feature-card">
                            <div class="feature-icon">
                                <i class="fas fa-mobile-alt"></i>
                            </div>
                            <h3>多设备适配</h3>
                            <p>完美适配电脑、平板和手机等各类设备</p>
                        </div>
                    </div>
                </section>
                
                <section class="playlist-section">
                    <div class="playlist-header">
                        <i class="fas fa-list"></i>
                        课程列表
                    </div>
                    <div class="playlist">
                        <div class="playlist-item active">
                            <div class="playlist-thumbnail">
                                <i class="fas fa-play-circle"></i>
                            </div>
                            <div class="playlist-info">
                                <div class="playlist-title">课件一：GemDesign 入门教程</div>
                                <div class="playlist-duration"><i class="far fa-clock"></i> 15:30</div>
                            </div>
                        </div>
                        <div class="playlist-item">
                            <div class="playlist-thumbnail">
                                <i class="fas fa-play-circle"></i>
                            </div>
                            <div class="playlist-info">
                                <div class="playlist-title">课件二：高级功能详解</div>
                                <div class="playlist-duration"><i class="far fa-clock"></i> 22:15</div>
                            </div>
                        </div>
                        <div class="playlist-item">
                            <div class="playlist-thumbnail">
                                <i class="fas fa-play-circle"></i>
                            </div>
                            <div class="playlist-info">
                                <div class="playlist-title">课件三：实战项目案例</div>
                                <div class="playlist-duration"><i class="far fa-clock"></i> 28:40</div>
                            </div>
                        </div>
                        <div class="playlist-item">
                            <div class="playlist-thumbnail">
                                <i class="fas fa-play-circle"></i>
                            </div>
                            <div class="playlist-info">
                                <div class="playlist-title">课件四：团队协作功能</div>
                                <div class="playlist-duration"><i class="far fa-clock"></i> 18:20</div>
                            </div>
                        </div>
                        <div class="playlist-item">
                            <div class="playlist-thumbnail">
                                <i class="fas fa-play-circle"></i>
                            </div>
                            <div class="playlist-info">
                                <div class="playlist-title">课件五：设计规范与最佳实践</div>
                                <div class="playlist-duration"><i class="far fa-clock"></i> 25:10</div>
                            </div>
                        </div>
                    </div>
                </section>
            </div>
        </main>
        
        <footer class="footer">
            <p>© 2023 GemDesign 视频课件中心 版权所有</p>
            <p>设计让世界更美好 | 学习让未来更精彩</p>
        </footer>
    </div>

    <script>
        // 获取DOM元素
        const video = document.getElementById('mainVideo');
        const playPauseBtn = document.getElementById('playPauseBtn');
        const progressBar = document.getElementById('progressBar');
        const progressContainer = document.getElementById('progressContainer');
        const currentTimeEl = document.getElementById('currentTime');
        const durationEl = document.getElementById('duration');
        const volumeBtn = document.getElementById('volumeBtn');
        const volumeSlider = document.getElementById('volumeSlider');
        const volumeLevel = document.getElementById('volumeLevel');
        const fullscreenBtn = document.getElementById('fullscreenBtn');
        const playlistItems = document.querySelectorAll('.playlist-item');
        
        // 播放/暂停功能
        function togglePlay() {
            if (video.paused) {
                video.play();
                playPauseBtn.innerHTML = '<i class="fas fa-pause"></i>';
            } else {
                video.pause();
                playPauseBtn.innerHTML = '<i class="fas fa-play"></i>';
            }
        }
        
        playPauseBtn.addEventListener('click', togglePlay);
        video.addEventListener('click', togglePlay);
        
        // 更新进度条
        function updateProgress() {
            const progressPercent = (video.currentTime / video.duration) * 100;
            progressBar.style.width = `${progressPercent}%`;
            
            // 更新时间显示
            currentTimeEl.textContent = formatTime(video.currentTime);
        }
        
        video.addEventListener('timeupdate', updateProgress);
        
        // 设置进度
        function setProgress(e) {
            const width = this.clientWidth;
            const clickX = e.offsetX;
            const duration = video.duration;
            
            video.currentTime = (clickX / width) * duration;
        }
        
        progressContainer.addEventListener('click', setProgress);
        
        // 格式化时间
        function formatTime(seconds) {
            let mins = Math.floor(seconds / 60);
            let secs = Math.floor(seconds % 60);
            
            if (mins < 10) mins = '0' + mins;
            if (secs < 10) secs = '0' + secs;
            
            return `${mins}:${secs}`;
        }
        
        // 设置视频时长
        video.addEventListener('loadedmetadata', () => {
            durationEl.textContent = formatTime(video.duration);
        });
        
        // 音量控制
        function toggleMute() {
            video.muted = !video.muted;
            
            if (video.muted) {
                volumeBtn.innerHTML = '<i class="fas fa-volume-mute"></i>';
                volumeLevel.style.width = '0%';
            } else {
                volumeBtn.innerHTML = '<i class="fas fa-volume-up"></i>';
                volumeLevel.style.width = '80%';
                video.volume = 0.8;
            }
        }
        
        volumeBtn.addEventListener('click', toggleMute);
        
        function setVolume(e) {
            const width = this.clientWidth;
            const clickX = e.offsetX;
            const volume = clickX / width;
            
            video.volume = volume;
            volumeLevel.style.width = `${volume * 100}%`;
            
            if (volume === 0) {
                volumeBtn.innerHTML = '<i class="fas fa-volume-mute"></i>';
            } else {
                volumeBtn.innerHTML = '<i class="fas fa-volume-up"></i>';
            }
        }
        
        volumeSlider.addEventListener('click', setVolume);
        
        // 全屏功能
        function toggleFullscreen() {
            if (!document.fullscreenElement) {
                if (video.requestFullscreen) {
                    video.requestFullscreen();
                } else if (video.webkitRequestFullscreen) {
                    video.webkitRequestFullscreen();
                } else if (video.msRequestFullscreen) {
                    video.msRequestFullscreen();
                }
                
                fullscreenBtn.innerHTML = '<i class="fas fa-compress"></i>';
            } else {
                if (document.exitFullscreen) {
                    document.exitFullscreen();
                } else if (document.webkitExitFullscreen) {
                    document.webkitExitFullscreen();
                } else if (document.msExitFullscreen) {
                    document.msExitFullscreen();
                }
                
                fullscreenBtn.innerHTML = '<i class="fas fa-expand"></i>';
            }
        }
        
        fullscreenBtn.addEventListener('click', toggleFullscreen);
        
        // 播放列表功能
        playlistItems.forEach(item => {
            item.addEventListener('click', () => {
                // 移除所有active类
                playlistItems.forEach(i => i.classList.remove('active'));
                // 添加active类到当前项
                item.classList.add('active');
                
                // 这里可以添加切换视频的逻辑
                // 例如：video.src = '新的视频路径';
            });
        });
        
        // 键盘快捷键
        document.addEventListener('keydown', (e) => {
            if (e.code === 'Space') {
                e.preventDefault();
                togglePlay();
            }
            
            if (e.code === 'ArrowLeft') {
                video.currentTime -= 5;
            }
            
            if (e.code === 'ArrowRight') {
                video.currentTime += 5;
            }
            
            if (e.code === 'ArrowUp') {
                if (video.volume < 0.95) {
                    video.volume += 0.05;
                } else {
                    video.volume = 1;
                }
                volumeLevel.style.width = `${video.volume * 100}%`;
            }
            
            if (e.code === 'ArrowDown') {
                if (video.volume > 0.05) {
                    video.volume -= 0.05;
                } else {
                    video.volume = 0;
                }
                volumeLevel.style.width = `${video.volume * 100}%`;
            }
            
            if (e.code === 'KeyM') {
                toggleMute();
            }
            
            if (e.code === 'KeyF') {
                toggleFullscreen();
            }
        });
        
        // 初始化音量
        video.volume = 0.8;
    </script>
</body>
</html>
