# playinsert
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
[![][discord-shield]][discord-link]
[![][github-license-shield]][github-license-link]
[![][github-stars-shield]][github-stars-link]

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

1. **🎮 Support for Self-Hosting with Nvidia, AMD, and Intel: Initially, we use Nvidia for game execution, ensuring extensive compatibility with various titles and providing a smooth, diverse gaming experience.

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
> If you're excited about what we're doing and want to support our journey, consider giving us a star ⭐ on our repository. Your support fuels our progress!. \~ ✨


[![][image-star]][github-stars-link]


## Getting Started 🎮

Whether you're looking to self-host playinsert or simply want to try it out without the need for your own GPU, we've got you covered. Choose the path that best suits your needs:

<!-- _You can always change your option later without losing game progress_ -->

| If you don't have a Nvidia GPU or prefer not to self-host, you can visit our website. No installation or set up required ! <br/> This is the perfect option for gamers looking to dive straight into the action without any setup. | [👉🏽 Get Access][website-link] |
| :---------------------------------------- | :----------------------------------------------------------------------------------------------------------------- |
| If you're interested in self-hosting playinser, continue reading for detailed instructions on how to get started. <br/> This option is ideal if you have your own Nvidia GPU and are comfortable with setting up and managing your own server. | [🛠️ Self Host playinser](#self-hosting) |

> \[!TIP]
>
> Remember, flexibility is key with playinsert. You're free to switch between self-hosting and using `playinser.app` whenever you like, without losing your game progress. \~ 💡
<a name="self-hosting"></a>

### Self-Hosting playinser 🔨

For those interested in self-hosting, here are is what you need to get your own playinser server up and running:

- **Nvidia GPU**: Unfortunately, this setup is exclusive to Nvidia GPUs. If you don't own one, consider renting from cloud services like AWS, GCP, or Vast.ai. We highly recommend this approach.

- **CUDA**: For GPU acceleration, CUDA version `12.0` or newer is required. Verify your CUDA installation by running `nvcc --version`.

- **Docker**: Ensure you have `docker` and `nvidia-docker` are up to date to avoid compatibility issues with CUDA. You can check your Docker version by running `docker --version` in your terminal.

- **GPU Driver**: Ensure your GPU drivers are up to date to avoid compatibility issues with CUDA. Nvidia driver version `520.56.06` or newer is required.

- **Xorg Display**: Your Nvidia GPU should not be attached to a running X display server. You can confirm this by running `nvidia-smi`.

- **Nvidia-DRM**: Make sure that the `nvidia-drm` module has been loaded and that the module is loaded with the flag `modeset=1`. Confirm this by running `sudo cat /sys/module/nvidia_drm/parameters/modeset` 

> \[!TIP]
>
> Typically, if your setup meets the necessary CUDA requirements, the `nvidia-drm` module will already be loaded, particularly in AWS G4dn instances. \~ 💡

### Step-by-Step Guide

Follow these steps to get playinser up and running on your system.

> \[!IMPORTANT]
>
> This is our pilot, there is a lot we haven't figured out yet. Please file an issue if anything comes up. \~ 🫂


> \[!TIP]
>
> The setup process will become much simpler with the launch of our CLI tool, so stay tuned for that! In the meantime, you'll need to follow these manual steps.

#### Step 1: Navigate to Your Game Directory

First, change your directory to the location of your `.exe` file. For Steam games, this typically means:

```bash
cd $HOME/.steam/steam/steamapps
ls -la .
```

#### Step 2: Generate a Session ID

Create a unique session ID using the following command:

```bash
head /dev/urandom | LC_ALL=C tr -dc 'a-zA-Z0-9' | head -c 16
```

This command generates a random 16-character string. Be sure to note this string carefully, as you'll need it for the next step.

#### Step 3: Launch the playinser Server

With your SESSION_ID ready, insert it into the command below, replacing `<copy here>` with your actual session ID. Then, run the command to start the playinsert server:

```
docker run --gpus all --device=/dev/dri --name playinsert -it --entrypoint /bin/bash -e SESSION_ID=<copy here> -v "$(pwd)":/game -p 8080:8080/udp --cap-add=SYS_NICE --cap-add=SYS_ADMIN ghcr.io/playinsertness/playinsert/server:nightly
```

> \[!TIP]
>
> Ensure UDP port 8080 is accessible from the internet. Use `ufw allow 8080/udp` or adjust your cloud provider's security group settings accordingly.

#### Step 4: Configure the Game within the Container

After executing the previous command, you'll be in a new shell within the container (example: `playinsert@3f199ee68c01:~$`). Perform the following checks:

1. Verify the game is mounted by executing `ls -la /game`. If not, exit and ensure you've correctly mounted the game directory as a volume.
2. Then, start the Netris server by running `/etc/startup.sh > /dev/null &`.

#### Step 5: Running Your Game

Wait for the `.X11-unix` directory to appear in `/tmp` (check with `ls -la /tmp`). Once it appears, you're ready to launch your game.

- With Proton-GE: `playinsert-proton -pr <game>.exe`
- With Wine: `playinsert-proton -wr <game>.exe`

#### Step 6: Begin Playing

Finally, construct the play URL with your session ID:

```
echo "https://playinsert.app/play/$SESSION_ID"
```

Navigate to this URL in your browser, click on the page to capture your mouse pointer, and start playing!


[github-release-link]: https://github.com/wanjohiryan/netris/releases
[github-release-shield]: https://img.shields.io/github/v/release/wanjohiryan/netris?color=369eff&labelColor=black&logo=github&style=flat-square
[discord-shield]: https://img.shields.io/discord/1080111004698021909?color=5865F2&label=discord&labelColor=black&logo=discord&logoColor=white&style=flat-square
[discord-link]: https://discord.com/invite/Y6etn3qKZ3
[github-license-shield]: https://img.shields.io/github/license/wanjohiryan/netris?color=white&labelColor=black&style=flat-square
[github-license-link]: https://github.com/wanjohiryan/netris/blob/main/LICENSE
[github-stars-shield]: https://img.shields.io/github/stars/wanjohiryan/netris?color=ffcb47&labelColor=black&style=flat-square
[github-stars-link]: https://github.com/wanjohiryan/netris/network/stargazers
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
