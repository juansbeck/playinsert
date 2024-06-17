# playinsert
The Future of Cloud Gaming: Open-Source, Social, and on Solana Blockchain

<div align="center">
<div>

<a href="https://nestri.io" >
<img height="160" src="/assets/logo.png">
</a>

</div>

&nbsp;
&nbsp;

<div align="center" >
<h1>
<a href="https://nestri.io" >
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="/assets/logo-name-white.png">
  <source media="(prefers-color-scheme: light)" srcset="/assets/logo-name-black.png">
  <img alt="nestri logo name" src="/assets/logo-name-black.png">
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

**Share the Nestri Repository on Social Media**

[![][share-x-shield]][share-x-link]
[![][share-reddit-shield]][share-reddit-link]

</div>
&nbsp;
&nbsp;

<div align="center" >

[![][image-overview]][website-link]

</div>

## Features 🌟

As Nestri navigates through its _experimental_ phase, we're in the process of crafting and testing a variety of features for you:

1. **🎮 Proton-GE Compatibility:** We utilize Proton-GE for running games, offering extensive game compatibility and ensuring you can play a wide variety of titles.

2. **⚡ QUIC Protocol:** For input and video/audio transmission, we use QUIC via [MoQ][moq-github-url] to significantly reduce latency on variable networks, ensuring crisp visuals without sacrificing data or increasing latency.

3. **🔗 Session IDs:** With a `SESSION_ID`, we seamlessly tie your game progress, achievements, and devices without the need for logging into [nestri.io][website-link]. Our public CDNs, currently located in Europe (eu-north-1) and the US (us-east-1), further reduce latency for friends playing together from afar. More locations are on the way!

4. **🔄 Automatic Game Progress Sync:** Like Stadia's state share, we automatically sync your game progress based on the *.exe file you're running, allowing you to share your progress with friends via a link.

5. **👫 Co-op Gameplay:** Play co-op with up to 8 people, or play single player by sharing mouse and keyboard inputs seamlessly (similar to [neko][neko-url]).

6. **🌐 Cross-Platform Play:** Our platform is accessible on any device that can run a Chrome-based browser, including Edge, Chrome, Brave, and Arc. And you do not have to set up anything, it's all done and maintained for you.

7. **📊 Bandwidth Optimization:** Experience hardware-accelerated `VMAF` for optimized bandwidth, ensuring the best possible video quality. [Learn More][vmaf-cuda-link]

8. **🌟 ...and more:** Stay tuned as we continue to add features _sometimes inspired by platforms like Stadia_, to give you the best and most customizable gaming experience.

This platform is in an _experimental_ phase, and we're actively working on adding new features. Your feedback and support is very much appreciated.

> \[!IMPORTANT]
>
> If you're excited about what we're doing and want to support our journey, consider giving us a star ⭐ on our repository. Your support fuels our progress!. \~ ✨


[![][image-star]][github-stars-link]


## Getting Started 🎮

Whether you're looking to self-host Nestri or simply want to try it out without the need for your own GPU, we've got you covered. Choose the path that best suits your needs:

<!-- _You can always change your option later without losing game progress_ -->

| If you don't have a Nvidia GPU or prefer not to self-host, you can visit our website. No installation or set up required ! <br/> This is the perfect option for gamers looking to dive straight into the action without any setup. | [👉🏽 Get Access][website-link] |
| :---------------------------------------- | :----------------------------------------------------------------------------------------------------------------- |
| If you're interested in self-hosting Nestri, continue reading for detailed instructions on how to get started. <br/> This option is ideal if you have your own Nvidia GPU and are comfortable with setting up and managing your own server. | [🛠️ Self Host Nestri](#self-hosting) |

> \[!TIP]
>
> Remember, flexibility is key with Nestri. You're free to switch between self-hosting and using `nestri.io` whenever you like, without losing your game progress. \~ 💡
<a name="self-hosting"></a>

### Self-Hosting Nestri 🔨

For those interested in self-hosting, here are is what you need to get your own Nestri server up and running:

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

Follow these steps to get Nestri up and running on your system.

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

#### Step 3: Launch the Nestri Server

With your SESSION_ID ready, insert it into the command below, replacing `<copy here>` with your actual session ID. Then, run the command to start the Nestri server:

```
docker run --gpus all --device=/dev/dri --name nestri -it --entrypoint /bin/bash -e SESSION_ID=<copy here> -v "$(pwd)":/game -p 8080:8080/udp --cap-add=SYS_NICE --cap-add=SYS_ADMIN ghcr.io/nestriness/nestri/server:nightly
```

> \[!TIP]
>
> Ensure UDP port 8080 is accessible from the internet. Use `ufw allow 8080/udp` or adjust your cloud provider's security group settings accordingly.

#### Step 4: Configure the Game within the Container

After executing the previous command, you'll be in a new shell within the container (example: `nestri@3f199ee68c01:~$`). Perform the following checks:

1. Verify the game is mounted by executing `ls -la /game`. If not, exit and ensure you've correctly mounted the game directory as a volume.
2. Then, start the Netris server by running `/etc/startup.sh > /dev/null &`.

#### Step 5: Running Your Game

Wait for the `.X11-unix` directory to appear in `/tmp` (check with `ls -la /tmp`). Once it appears, you're ready to launch your game.

- With Proton-GE: `nestri-proton -pr <game>.exe`
- With Wine: `nestri-proton -wr <game>.exe`

#### Step 6: Begin Playing

Finally, construct the play URL with your session ID:

```
echo "https://nestri.io/play/$SESSION_ID"
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
[website-link]: https://nestri.io
[neko-url]: https://github.com/m1k1o/neko
[image-star]: assets/star-us.png
[moq-github-url]: https://quic.video
[vmaf-cuda-link]: https://developer.nvidia.com/blog/calculating-video-quality-using-nvidia-gpus-and-vmaf-cuda/
