
---
title: 获取原始音视频数据
description: 
platform: Linux
updatedAt: Thu Mar 05 2020 03:22:53 GMT+0800 (CST)
---
# 获取原始音视频数据
Agora 本地服务端录制 SDK 目前支持单流模式下的原始音视频数据，以及合流模式下音频混音后的原始音频数据。

录制模式与录制内容的设置，详见[单流录制](../../cn/Recording/recording_individual_mode.md)和[合流录制](../../cn/Recording/recording_composite_mode.md)。

## 单流模式下录制原始音视频数据

设置参数 `isMixingEnabled` = 0，即启动单流模式录制。 

你可以根据需要生成的文件类型，选择不同的录制模式：

| 录制内容     | 命令行录制                                                   | 调用 API 录制                                                |
| :----------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| 原始音频数据 | <li>`--getAudioFrame 1`: AAC 格式<li>`--getAudioFrame 2`: PCM 格式 | <li>`decodeAudio = 1`: AAC 格式<li>`decodeAudio = 2`: PCM 格式     |
| 原始视频数据 | <li>`--getVideoFrame 1`: H.264 帧格式<li>`--getVideoFrame 2`: YUV 帧格式<li>`--getVideoFrame 3`: JPG 帧格式<li>`--getVideoFrame 4`: JPG 文件格式<li>`--getVideoFrame 5`: JPG 文件格式 + MP4 视频文件格式 | <li>`decodeVideo = 1`: H.264 帧格式<li>`decodeVideo = 2`: YUV 帧格式<li>`decodeVideo = 3`: JPG 帧格式<li>`decodeVideo = 4`: JPG 文件格式<li>`decodeVideo = 5`: JPG 文件格式 + MP4 视频文件格式 |

> Web 端不支持 H.264 的原始音视频数据，支持 YUV 的原始音视频数据。
	
当收到原始音频和视频数据时，会分别触发 `videoFrameReceived` 和 `audioFrameReceived` 回调，回调中包含原始音频和视频数据。

## 合流模式下录制原始音视频数据
	
设置参数 `isMixingEnabled` = 1，即启动合流模式录制。 

Agora 本地服务端录制 SDK 目前仅支持多个音频流混音后的原始音频数据，并生成 PCM 文件。

| 录制内容     | 命令行录制                             | 调用 API 录制                       |
| :----------- | :------------------------------------- | :---------------------------------- |
| 原始音频数据 | `--getAudioFrame 3`：PCM 混音格式 | `decodeAudio = 3`：PCM 混音格式 |

	
当收到原始音频数据时，会触发 `audioFrameReceived`  回调，回调中包含原始音频数据。

