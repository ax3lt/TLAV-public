<div align="center">

# 🎬 StreamAnnouncer for Velocity

### Announce Twitch and Kick streams across your Minecraft network

[![Velocity](https://img.shields.io/badge/Velocity-3.3.0+-00AA00?style=for-the-badge&logo=minecraft&logoColor=white)](https://papermc.io/software/velocity)
[![Twitch](https://img.shields.io/badge/Twitch-Supported-9146FF?style=for-the-badge&logo=twitch&logoColor=white)](https://twitch.tv)
[![Discord](https://img.shields.io/discord/1166265613241569381?style=for-the-badge&logo=discord&logoColor=white&label=Discord&color=5865F2)](https://discord.com/invite/H2nsh8MNtr)

[![Free Premium Evaluation](https://img.shields.io/badge/Premium-Free%20Evaluation%20Copy-FF75D8?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/invite/H2nsh8MNtr)

</div>

---

This repository is the public home for **StreamAnnouncer**: it hosts the
**StreamAnnouncer-Bridge** downloads and the full feature list for both editions.
The plugin itself is distributed through the links below.

## 📥 Where to get it

| Edition | Where | Price |
|:--|:--|:--|
| **Lite** | [Modrinth](https://modrinth.com/plugin/streamannouncer-velocity-lite) | Free |
| **Premium** | [Ask on Discord](https://discord.com/invite/H2nsh8MNtr) | Paid, **free evaluation copy on request** |
| **Bridge** (companion) | [Releases](https://github.com/ax3lt/StreamAnnouncer-public/releases) | Free, requires Premium on the proxy |

> 🎁 **Want to try Premium before paying?** Message me on
> [Discord](https://discord.com/invite/H2nsh8MNtr) and I will send you a free
> evaluation copy. No payment, no commitment. Run it on your own network and decide.

---

## 📊 Lite vs Premium

| Feature | Lite (Free) | Premium |
|:--------|:-----------:|:-------:|
| **Twitch** live/offline announcements | ✅ | ✅ |
| **Kick** live/offline announcements | ❌ | ✅ |
| Smart filters (game & title) | ✅ | ✅ |
| Player self-service (`/setchannel`) | ✅ | ✅ |
| Admin channel management | ✅ | ✅ |
| MiniMessage formatting | ✅ | ✅ |
| Auto update checker | ✅ | ✅ |
| **Reward automation** (commands on start/stop/during) | ❌ | ✅ |
| **Channel-specific commands** | ❌ | ✅ |
| **Timed rewards** while streaming | ❌ | ✅ |
| **MySQL** cross-server sync | ❌ | ✅ |
| **PlaceholderAPI** integration | ❌ | ✅ |
| **Multi-stream viewer** links | ❌ | ✅ |
| **Plugin messaging bridge** (backend server commands) | ❌ | ✅ |
| **HMAC-signed** secure messaging | ❌ | ✅ |
| **Streamer join** announcements | ❌ | ✅ |

---

## ✅ In both editions

- **Twitch live and offline announcements**, broadcast to the servers you choose
  (`broadcast_in_servers`), formatted with MiniMessage.
- **Filters** so only the streams you care about are announced: by game
  (`filter_stream_type`) and by stream title (`filter_stream_title`).
- **Account linking** between a Minecraft player and one or more channels, managed by
  players themselves or by staff. Links survive a rename through
  `/sav link transfer <old> <new>`.
- **Admin commands** for channels, links and reloading configuration, all under `/sav`.
- **Update checker**, which can be switched off.

## 🔒 Premium only, in detail

The config keys are named so you can see exactly what you would be configuring.

### 🟢 Kick support
A second platform alongside Twitch with its own `kick.yml`: channel list, linked users,
filters and messages. Lite is Twitch only.

### 🎁 Reward commands on stream start and stop
`commands` in `twitch.yml` / `kick.yml`. Runs a list of commands when a channel goes
live, and another when it stops, once **per linked Minecraft player**. Placeholders:
`%player%`, `%channel%`, `%title%`, `%platform%`. Every command targets the servers you
name, and `skip_offline_players` avoids firing for players who are not connected.

### 🎯 Per-channel commands
`channelCommands`. The same start/stop hooks defined **per channel**, so a partnered
streamer can trigger different rewards from everyone else.

### ⏱️ Timed rewards while live
`timedCommands`. Repeats commands every `repeat_time` seconds (set in `config.yml`) for
as long as the streamer stays live, for each linked player. The shipped example is
`give %player% minecraft:diamond 1`.

### 🔗 Multi-stream viewer link
`multiPlatformViewer`. Combines **every** channel currently live, across Twitch and Kick,
into one shareable URL and broadcasts it on an interval to the servers you choose. The
URL format is configurable, with working presets for multiwatch.net and multistream.me.

### 🗄️ MySQL sync
Writes live state into three tables (`liveChannels`, `placeholders`, `linkedUsers`) so
backend servers and other plugins can read who is live without talking to the proxy.

### 🔌 StreamAnnouncer-Bridge and PlaceholderAPI
A companion plugin for backend Paper/Spigot servers, downloadable from this repository's
[releases](https://github.com/ax3lt/StreamAnnouncer-public/releases). The proxy sends
commands over a plugin messaging channel and every message is signed with **HMAC-SHA256**
using the `shared-secret` from `config.yml`, so a backend server will not act on a forged
packet. PlaceholderAPI then exposes live status for scoreboards, tab lists and chat
prefixes.

### 👋 Announce when the streamer joins
`announce_only_if_streamer_on_server`. Holds the announcement back until the linked player
is actually on the network, then announces, so nobody misses it because the streamer went
live before joining.

---

## 💬 Support

[![Discord Server](https://img.shields.io/discord/1166265613241569381?style=for-the-badge&logo=discord&logoColor=white&label=Join%20Our%20Discord&color=5865F2)](https://discord.com/invite/H2nsh8MNtr)

Questions, bug reports and premium evaluation requests all go to Discord.
