# 🌟playinsert.app🕹️
                             The Future of Cloud Gaming: Open-Source, Social, and on Solana Blockchain

<div align="center">
<div>

<a href="https://playinsert.app" >
<img height="160" src="/assets/logo.png">
</a>

</div>

&nbsp;
&nbsp;

<div align="center" >
<h1>
<a href="https://playinsert.app" >
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/assets/logo-name-white.png">
  <source media="(prefers-color-scheme: light)" srcset="/assets/logo-name-black.png">
  <img alt="playinsert logo name" src="/assets/logo-name-black.png">
</picture>

</a>

</h1>

</div>
&nbsp;
&nbsp;

An open-source cloud gaming platform built for you to play together with your friends. <br/> A GeForce NOW alternative that can be self-hosted.<br/>

</div>

&nbsp;
&nbsp;
 <div align="center" >

[![][github-release-shield]][github-release-link]
[![][github-license-shield]][github-license-link]


**Share the playinsert Repository on Social Media**

[![][share-x-shield]][share-x-link]
[![][share-reddit-shield]][share-reddit-link]

</div>
&nbsp;
&nbsp;

<div align="center" >

[![][image-overview]][website-link]

</div>

## Innovate Features 🚀

As PlayInsert progresses through its pilot phase, we are designing and testing a wide range of capabilities for you::

1. **🕹️ Support for Self-Hosting with Nvidia, AMD, and Intel: Initially, we use Nvidia for game execution, ensuring extensive compatibility with various titles and providing a smooth, diverse gaming experience.

2. **⚡ H.265/HEVC Encoding: For video/audio input and transmission, we utilize x265/AV1 via Nvenc. To drastically minimize latency on unstable networks, we have developed our proprietary UFI routing system, delivering crisp images without compromising data or increasing latency.

3. **🔗 Triple A: With a SESSION_ID, we seamlessly link your game progress, achievements, and devices without needing to log in to [playinsert.app][website-link]. Our public content delivery networks (CDNs) with UFI routing further reduce latency for friends playing together from remote locations!

4. **🔄 Deep Linking: Allows users to navigate directly to specific content within the application from external links. These links can be shared through various means, such as emails, text messages, or messaging platforms like Telegram, WhatsApp, Twitter, and WeChat. Automatic synchronization of game progress: similar to the shared state in Stadia, we automatically sync your game progress across devices, allowing you to switch from your mobile to your TV, tablet, or PC and share your progress with friends via a link.

5. **👥 Collaborative Gaming: Participate in cooperative games with up to 8 players.

6. **🌐 Cross-Platform Gaming: Our platform is accessible from any device running Android, iOS, Windows, Linux, with no additional configuration needed; everything is pre-set and maintained for you.

7. **📊 Bandwidth Optimization: Experience hardware-accelerated UFI with optimized bandwidth usage, ensuring the best data routing and the highest possible video quality, maximizing bandwidth utilization without sacrificing bitrate. Learn more. [Learn More][vmaf-cuda-link]

8. **🛡️ Security and Privacy: We implement end-to-end encryption on all data transmissions, ensuring your information and game progress are always protected against unauthorized access.

9. **🔧 Advanced Customization: We offer customization options to adjust graphic and performance settings according to your preferences and your device's capabilities, allowing you to optimize your gaming experience.

10. **🌟 ...and more:** Stay tuned as we continue to add features _sometimes inspired by platforms like Stadia_, to give you the best and most customizable gaming experience.

This platform is in an _experimental_ phase, and we're actively working on adding new features. Your feedback and support is very much appreciated.

> \[!IMPORTANT]
>
> If you're thrilled about what we're doing and want to support our project, consider giving us a star 🌟 on our repository. Your support drives our progress! ✨


[![][image-star]][github-stars-link]


## Getting Started 🕹️

Whether you wish to host PlayInsert yourself or simply want to try it out without needing your own GPU, we've got everything you need. Choose the option that best aligns with your preferences:

<!-- _You can always alter your choice later without forfeiting game progress_ -->

| If you lack an Nvidia GPU or prefer not to self-host, you can visit our website. No installation or configuration needed ! <br/>This is the ideal choice for gamers who want to sign up first and receive notifications when the service becomes available. | [👉🏽 Get Access][website-link] |
| :---------------------------------------- | :----------------------------------------------------------------------------------------------------------------- |
| If you're interested in self-hosting PlayInsert, keep reading for detailed instructions on how to get started. <br/> This choice is ideal if you have your own Nvidia GPU and are comfortable setting up and managing your own server. You'll need to sign up to receive notifications about the availability of self-hosting. | [🛠️ Self Host playinsert](#self-hosting) |

> \[!TIP]
>
> Remember, flexibility is crucial with PlayInsert. You can switch between self-hosting and using `playinser.app` at any time, without losing your game progress. \~ 💡
<a name="self-hosting"></a>

### Self-Hosting playinsert 🔨

If you're considering self-hosting, stay tuned to our official channels as we'll announce when you can start with self-hosting. Here's what you need to get your own PlayInsert server up and running::

- **GPU** Nvidia, AMD, or Intel ARC GPU: If you don't have one, you can rent one from cloud services like AWS or Google Cloud. We highly recommend this approach.

- **CUDA**: For GPU acceleration on Linux, CUDA version `12.0` or higher is required. Verify your CUDA installation by running `nvcc --version`.

- **Docker**: Ensure your `docker` and `nvidia-docker` are up-to-date to avoid CUDA compatibility issues. Check your Docker version by running`docker --version` in your terminal.

- **GPU Drivers**: Ensure your GPU drivers are up-to-date to avoid CUDA compatibility issues. Nvidia driver version `520.56.06` or later is required.

- **Xorg Display**: Ensure your Nvidia GPU isn't connected to a running Xorg display server. Confirm this by running `nvidia-smi`.

- **Nvidia-DRM**: Make sure that the `nvidia-drm` module has been loaded and that the module is loaded with the flag `modeset=1`. Confirm this by running `sudo cat /sys/module/nvidia_drm/parameters/modeset` 

> \[!TIP]
>
> Typically, if your setup meets the necessary CUDA requirements, the nvidia-drm module will already be loaded, particularly on AWS G4dn instances. \~ 💡

### Step-by-Step Guide

Follow these steps to get playinsert up and running on your system.

> \[!IMPORTANT]
>
> This is our pilot, there is a lot we haven't figured out yet. Please file an issue if anything comes up. \~ 🫂


> \[!TIP]
>
> The setup process will become much simpler with the launch of our CLI tool, so stay tuned for that! In the meantime, you'll need to follow these manual steps.



[github-release-link]: https://github.com/wanjohiryan/netris/releases
[github-release-shield]: https://img.shields.io/github/v/release/wanjohiryan/netris?color=369eff&labelColor=black&logo=github&style=flat-square
[discord-shield]: https://img.shields.io/discord/1080111004698021909?color=5865F2&label=discord&labelColor=black&logo=discord&logoColor=white&style=flat-square
[discord-link]: https://discord.com/invite/Y6etn3qKZ3
[github-license-shield]: https://img.shields.io/github/license/wanjohiryan/netris?color=white&labelColor=black&style=flat-square
[github-license-link]: https://github.com/wanjohiryan/netris/blob/main/LICENSE
[github-stars-shield]: https://img.shields.io/github/stars/wanjohiryan/netris?color=ffcb47&labelColor=black&style=flat-square
[share-x-shield]: https://img.shields.io/badge/-share%20on%20x-black?labelColor=black&logo=x&logoColor=white&style=flat-square
[share-x-link]: https://twitter.com/intent/tweet?text=Hey%2C%20check%20out%20this%20Github%20repository.%20It%20is%20an%20open-source%20self-hosted%20Geforce%20Now%20alternative.&url=https%3A%2F%2Fgithub.com%2Fwanjohiryan%2Fnetris
[share-reddit-shield]: https://img.shields.io/badge/-share%20on%20reddit-black?labelColor=black&logo=reddit&logoColor=white&style=flat-square
[share-reddit-link]: https://www.reddit.com/submit?title=Hey%2C%20check%20out%20this%20Github%20repository.%20It%20is%20an%20open-source%20self-hosted%20Geforce%20Now%20alternative.&url=https%3A%2F%2Fgithub.com%2Fwanjohiryan%2Fnetris
[image-overview]: assets/banner.png
[website-link]: https://playinsert.app
[neko-url]: https://github.com/m1k1o/neko
[image-star]: assets/star-us.png
[moq-github-url]: https://quic.video
[vmaf-cuda-link]: https://developer.nvidia.com/blog/calculating-video-quality-using-nvidia-gpus-and-vmaf-cuda/
