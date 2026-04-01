# 广告创意的生成式 AI 工具

这是一份参考清单，帮助你用 AI 图片生成器、视频生成器和代码驱动的视频工具，规模化生产广告视觉素材。

---

## 生成式工具适用场景

| 需求 | 工具类别 | 最适合 |
|------|---------------|----------|
| 静态广告图（横幅、社媒） | 图片生成 | Nano Banana Pro、Flux、Ideogram |
| 带文字叠层的广告图 | 图片生成（擅长文字） | Ideogram、Nano Banana Pro |
| 短视频广告（6 到 30 秒） | 视频生成 | Veo、Kling、Runway、Sora、Seedance |
| 带旁白的视频广告 | 视频生成 + 语音 | Veo / Sora（原生），或 Runway + ElevenLabs |
| 广告旁白音轨 | 语音生成 | ElevenLabs、OpenAI TTS、Cartesia |
| 多语言广告版本 | 语音生成 | ElevenLabs、PlayHT |
| 品牌声音克隆 | 语音生成 | ElevenLabs、Resemble AI |
| 产品 mockup 与变体 | 图片生成 + 参考图 | Flux（多图参考） |
| 模板化批量视频广告 | 代码驱动视频 | Remotion |
| 个性化视频（姓名、数据） | 代码驱动视频 | Remotion |
| 品牌一致的多版本素材 | 图片生成 + 风格参考 | Flux、Ideogram、Nano Banana Pro |

---

## 图片生成

### Nano Banana Pro (Gemini)

Google DeepMind 的图片生成模型，可通过 Gemini API 使用。

**最适合：** 高质量广告图片、产品视觉、图片中的文字渲染
**API:** Gemini API (Google AI Studio, Vertex AI)
**Pricing:** ~$0.04/image (Gemini 2.5 Flash Image), ~$0.24/4K image (Nano Banana Pro)

**优势：**
- Strong text rendering in images (logos, headlines)
- Native image editing (modify existing images with prompts)
- 可直接复用与文本生成相同的 Gemini API
- Supports both generation and editing in one model

**广告创意用例：**
- 根据文字描述生成社媒广告图
- 生成多种产品 mockup 版本
- 编辑已有广告图，例如替换背景、调整颜色
- 直接生成带标题文字的图片

**API 示例:**
```bash
# Using the Gemini API for image generation
curl -X POST "https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-image:generateContent" \
  -H "Content-Type: application/json" \
  -H "x-goog-api-key: $GEMINI_API_KEY" \
  -d '{
    "contents": [{"parts": [{"text": "Create a clean, modern social media ad image for a project management tool. Show a laptop with a kanban board interface. Bright, professional, 16:9 ratio."}]}],
    "generationConfig": {"responseModalities": ["TEXT", "IMAGE"]}
  }'
```

**Docs:** [Gemini Image Generation](https://ai.google.dev/gemini-api/docs/image-generation)

---

### Flux（Black Forest Labs）

开放权重的图片生成模型，可通过 Replicate 和 BFL 官方 API 使用。

**最适合：** 拟真图像、品牌一致的多版本产出、多参考图生成
**API:** Replicate, BFL API, fal.ai
**Pricing:** ~$0.01-0.06/image depending on model and resolution

**模型版本：**
| Model | Speed | 质量 | Cost | Best For |
|-------|-------|---------|------|----------|
| Flux 2 Pro | ~6 sec | Highest | $0.015/MP | Final production assets |
| Flux 2 Flex | ~22 sec | High + editing | $0.06/MP | Iterative editing |
| Flux 2 Dev | ~2.5 sec | Good | $0.012/MP | Rapid prototyping |
| Flux 2 Klein | Fastest | Good | Lowest | High-volume batch generation |

**优势：**
- 支持最多 8 张参考图，方便在多条广告里保持统一形象
- 产品一致性强，同一产品可以放进不同场景
- 支持从参考图迁移风格
- Dev 模型开源，可自托管

**广告创意用例：**
- 一次生成 50+ 个广告版本，同时保持人物或产品一致
- 生成“产品在具体使用场景中”的图片，例如 SaaS 出现在不同设备里
- 用参考图去贴合已有品牌资产的视觉风格
- 快速产出 A/B 测试用图片版本

**Docs:** [Replicate Flux](https://replicate.com/black-forest-labs/flux-2-pro), [BFL API](https://docs.bfl.ml/)

---

### Ideogram

专门强化图片中的排版与文字渲染。

**最适合：** 含文字的广告横幅、品牌图形、带标题的社媒广告图
**API:** Ideogram API, Runware
**Pricing:** ~$0.06/image (API), ~$0.009/image (subscription)

**优势：**
- Best-in-class text rendering (~90% accuracy vs ~30% for most tools)
- Style 参考 system (upload up to 3 参考 images)
- 4.3 billion style presets for consistent brand aesthetics
- Strong at logos and branded typography

**广告创意用例：**
- 直接生成内含标题文字的广告横幅
- 产出带品牌文字叠层的社媒图形
- 快速生成多版且排版风格一致的设计
- 在每次迭代都不依赖设计师的情况下产出推广素材

**Docs:** [Ideogram API](https://developer.ideogram.ai/), [Ideogram](https://ideogram.ai/)

---

### 其他图片工具

| 工具 | 最适合 | API 状态 | 说明 |
|------|----------|------------|-------|
| **DALL-E 3** (OpenAI) | General image generation | Official API | Integrated with ChatGPT, good text rendering |
| **Midjourney** | Artistic, high-aesthetic images | No official public API | Discord-based; unofficial APIs exist but risk bans |
| **Stable Diffusion** | 自托管、可深度定制 | 开源 | 更适合有 GPU 基础设施的团队 |

---

## 视频生成

### Google Veo

Google DeepMind 的视频生成模型，可通过 Gemini API 和 Vertex AI 使用。

**最适合：** 高质量带原生音频的视频广告，以及面向社媒的竖屏视频
**API:** Gemini API, Vertex AI
**Pricing:** ~$0.15/sec (Veo 3.1 Fast), ~$0.40/sec (Veo 3.1 Standard)

**能力:**
- Up to 60 seconds at 1080p
- Native audio generation (dialogue, sound effects, ambient)
- Vertical 9:16 output for Stories/Reels/Shorts
- Upscale to 4K
- Text-to-视频 and image-to-视频

**广告创意用例：**
- 从文字描述生成 15 到 30 秒短视频广告
- 为 TikTok、Reels、Shorts 生成竖屏广告
- 生成带旁白的产品演示视频
- 基于同一提示词，快速产出多种风格版本

**Docs:** [Veo on Vertex AI](https://cloud.google.com/vertex-ai/generative-ai/docs/video/overview)

---

### Kling（快手）

支持音视频同时生成，并带镜头控制能力。

**最适合：** 电影感广告视频、较长的视频内容、音画同步视频
**API:** Kling API, PiAPI, fal.ai
**Pricing:** ~$0.09/sec (via fal.ai third-party)

**能力:**
- Up to 3 minutes at 1080p/30-48fps
- Simultaneous audio-visual generation (Kling 2.6)
- Text-to-视频 and image-to-视频
- Motion and camera controls

**广告创意用例：**
- 更长的产品讲解视频
- 带同步音频的品牌电影感视频
- 把产品静态图转成视频广告

**Docs:** [Kling AI Developer](https://klingai.com/global/dev/model/video)

---

### Runway

一体化的视频生成与编辑平台，控制力较强。

**最适合：** 可控的视频生成、风格一致的内容、已有素材的再编辑
**API:** Runway Developer Portal

**能力:**
- Gen-4: Character/scene consistency across shots
- Motion brush and camera controls
- Image-to-视频 with 参考 images
- 视频-to-视频 style transfer

**广告创意用例：**
- 生成跨镜头保持人物或产品一致的视频广告
- 把已有视频做风格迁移，贴近品牌视觉
- 延展或重混已有视频素材

**Docs:** [Runway API](https://docs.dev.runwayml.com/)

---

### Sora 2（OpenAI）

OpenAI 的视频生成模型，支持同步音频。

**最适合：** 高保真、带对白和音效的视频
**API:** OpenAI API
**Pricing:** Free tier available; Pro from $0.10-0.50/sec depending on resolution

**能力:**
- Up to 60 seconds with synchronized audio
- Dialogue, sound effects, and ambient audio
- sora-2 (fast) and sora-2-pro (质量) variants
- Text-to-视频 and image-to-视频

**广告创意用例：**
- 视频推荐语与 talking-head 风格广告
- 带讲解的产品 Demo 视频
- 叙事型品牌视频

**Docs:** [OpenAI Video Generation](https://platform.openai.com/docs/guides/video-generation)

---

### Seedance 2.0 (ByteDance)

ByteDance's 视频 generation model with simultaneous audio-visual generation and multimodal inputs.

**Best for:** Fast, affordable 视频 ads with native audio, multimodal 参考 inputs
**API:** BytePlus (official), Replicate, WaveSpeedAI, fal.ai (third-party); OpenAI-compatible API format
**Pricing:** ~$0.10-0.80/min depending on resolution (estimated 10-100x cheaper than Sora 2 per clip)

**能力:**
- Up to 20 seconds at up to 2K resolution
- Simultaneous audio-visual generation (Dual-Branch Diffusion Transformer)
- Text-to-视频 and image-to-视频
- Up to 12 参考 files for multimodal input
- OpenAI-compatible API structure

**Ad creative use cases:**
- High-volume short 视频 ad production at low cost
- 视频 ads with synchronized voiceover and sound effects in one pass
- Multi-参考 generation (feed 产品 images, brand assets, style references)
- Rapid iteration on 视频 ad 概念

**Docs:** [Seedance](https://seed.bytedance.com/en/seedance2_0)

---

### Higgsfield

Full-stack 视频 creation 平台 with cinematic camera controls.

**Best for:** Social 视频 ads, cinematic style, mobile-first content
**平台:** [higgsfield.ai](https://higgsfield.ai/)

**能力:**
- 50+ professional camera movements (zooms, pans, FPV drone shots)
- Image-to-视频 animation
- Built-in editing, transitions, and keyframing
- All-in-one 工作流: image gen, animation, editing

**Ad creative use cases:**
- Social media 视频 ads with cinematic feel
- Animate 产品 images into dynamic 视频
- Create multiple 视频 variations with different camera styles
- Quick-turn 视频 content for social 广告活动

---

### 视频 工具 Comparison

| Tool | Max Length | Audio | Resolution | API | Best For |
|------|-----------|-------|------------|-----|----------|
| **Veo 3.1** | 60 sec | Native | 1080p/4K | Gemini | Vertical social 视频 |
| **Kling 2.6** | 3 min | Native | 1080p | Third-party | Longer cinematic |
| **Runway Gen-4** | 10 sec | No | 1080p | Official | Controlled, consistent |
| **Sora 2** | 60 sec | Native | 1080p | Official | Dialogue-heavy |
| **Seedance 2.0** | 20 sec | Native | 2K | Official + third-party | Affordable high-volume |
| **Higgsfield** | Varies | Yes | 1080p | Web-based | Social, mobile-first |

---

## Voice & Audio Generation

For layering realistic voiceovers onto 视频 ads, adding narration to 产品 demos, or generating audio for Remotion-rendered videos. These tools turn ad scripts into natural-sounding voice tracks.

### 适用场景 Voice Tools

Many 视频 generators (Veo, Kling, Sora, Seedance) now include native audio. Use standalone voice tools when you need:

- **Voiceover on silent 视频** — Runway Gen-4 and Remotion produce silent output
- **Brand voice consistency** — Clone a specific voice for all ads
- **Multi-language versions** — Same ad script in 20+ languages
- **Script iteration** — Re-record voiceover without reshooting 视频
- **Precise control** — Exact timing, emotion, and pacing

---

### ElevenLabs

The market leader in realistic voice generation and voice cloning.

**Best for:** Most natural-sounding voiceovers, brand voice cloning, multilingual
**API:** REST API with streaming support
**Pricing:** ~$0.12-0.30 per 1,000 characters depending on plan; starts at $5/month

**能力:**
- 29+ languages with natural accent and intonation
- Voice cloning from short audio clips (instant) or longer recordings (professional)
- Emotion and style control
- Streaming for real-time generation
- Voice library with hundreds of pre-built voices

**Ad creative use cases:**
- Generate voiceover tracks for 视频 ads
- Clone your brand spokesperson's voice for all ad variations
- Produce the same ad in 10+ languages from one script
- A/B test different voice styles (authoritative vs. friendly vs. urgent)

**API 示例:**
```bash
curl -X POST "https://api.elevenlabs.io/v1/text-to-speech/{voice_id}" \
  -H "xi-api-key: $ELEVENLABS_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "text": "Stop wasting hours on manual reporting. Try DataFlow free for 14 days.",
    "model_id": "eleven_multilingual_v2",
    "voice_settings": {"stability": 0.5, "similarity_boost": 0.75}
  }' --output voiceover.mp3
```

**Docs:** [ElevenLabs API](https://elevenlabs.io/docs/api-reference/text-to-speech)

---

### OpenAI TTS

Simple, affordable text-to-speech built into the OpenAI API.

**Best for:** Quick voiceovers, cost-effective at scale, simple integration
**API:** OpenAI API (same SDK as GPT/DALL-E)
**Pricing:** $15/million chars (standard), $30/million chars (HD); ~$0.015/min with gpt-4o-mini-tts

**能力:**
- 13 built-in voices (no custom cloning)
- Multiple languages
- Real-time streaming
- HD 质量 option
- Simple API — same SDK you already use for GPT

**Ad creative use cases:**
- Fast, cheap voiceover for draft/test ad versions
- High-volume narration at low cost
- Prototype ad audio before investing in premium voice

**Docs:** [OpenAI TTS](https://platform.openai.com/docs/guides/text-to-speech)

---

### Cartesia Sonic

Ultra-low latency voice generation built for real-time applications.

**Best for:** Real-time voice, lowest latency, emotional expressiveness
**API:** REST + WebSocket streaming
**Pricing:** Starts at $5/month; pay-as-you-go from $0.03/min

**能力:**
- 40ms time-to-first-audio (fastest in class)
- 15+ languages
- Nonverbal expressiveness: laughter, breathing, emotional inflections
- Sonic Turbo for even lower latency
- Streaming API for real-time generation

**Ad creative use cases:**
- Real-time ad preview during creative iteration
- Interactive demo videos with dynamic narration
- Ads requiring natural laughter, sighs, or emotional reactions

**Docs:** [Cartesia Sonic](https://docs.cartesia.ai/build-with-cartesia/tts-models/latest)

---

### Voicebox (Open 来源)

Free, local-first voice synthesis studio powered by Qwen3-TTS. The 开源 alternative to ElevenLabs.

**Best for:** Free voice cloning, local/private generation, zero-cost batch production
**API:** Local REST API at `http://localhost:8000`
**Pricing:** Free (MIT license). Runs entirely on your machine.
**Stack:** Tauri (Rust) + React + FastAPI (Python)

**能力:**
- Voice cloning from short audio samples via Qwen3-TTS
- Multi-language support (English, Chinese, more planned)
- Multi-track timeline editor for composing conversations
- 4-5x faster inference on Apple Silicon via MLX Metal acceleration
- Local REST API for programmatic generation
- No cloud dependency — all processing on-device

**Ad creative use cases:**
- Free voice cloning for brand spokesperson across all ad variations
- Batch generate voiceovers without per-character costs
- Private/local generation when ad content is sensitive or pre-launch
- Prototype voice variations before committing to a paid service

**API 示例:**
```bash
curl -X POST http://localhost:8000/generate \
  -H "Content-Type: application/json" \
  -d '{"text": "Stop wasting hours on manual reporting.", "profile_id": "abc123", "language": "en"}'
```

**Install:** Desktop apps for macOS and Windows at [voicebox.sh](https://voicebox.sh), or build from 来源:
```bash
git clone https://github.com/jamiepine/voicebox.git
cd voicebox && make setup && make dev
```

**Docs:** [GitHub](https://github.com/jamiepine/voicebox)

---

### Other Voice Tools

| Tool | Best For | Differentiator | API |
|------|----------|---------------|-----|
| **PlayHT** | Large voice library, low latency | 900+ voices, <300ms latency, ultra-realistic | [play.ht](https://play.ht/) |
| **Resemble AI** | Enterprise voice cloning | On-premise deployment, real-time speech-to-speech | [resemble.ai](https://www.resemble.ai/) |
| **WellSaid Labs** | Ethical, commercial-safe voices | Voices from compensated actors, safe for commercial use | [wellsaid.io](https://www.wellsaid.io/) |
| **Fish Audio** | 预算-friendly, emotion control | ~50-70% cheaper than ElevenLabs, emotion tags | [fish.audio](https://fish.audio/) |
| **Murf AI** | Non-technical teams | Browser-based studio, 200+ voices | [murf.ai](https://murf.ai/) |
| **Google Cloud TTS** | Google ecosystem, scale | 220+ voices, 40+ languages, enterprise SLAs | [Google TTS](https://cloud.google.com/text-to-speech) |
| **Amazon Polly** | AWS ecosystem, cost | Neural voices, SSML control, cheap at volume | [Amazon Polly](https://aws.amazon.com/polly/) |

---

### Voice 工具 Comparison

| Tool | 质量 | Cloning | Languages | Latency | Price/1K chars |
|------|---------|---------|-----------|---------|----------------|
| **ElevenLabs** | Best | Yes (instant + pro) | 29+ | ~200ms | $0.12-0.30 |
| **OpenAI TTS** | Good | No | 13+ | ~300ms | $0.015-0.030 |
| **Cartesia Sonic** | Very good | No | 15+ | ~40ms | ~$0.03/min |
| **PlayHT** | Very good | Yes | 140+ | <300ms | ~$0.10-0.20 |
| **Fish Audio** | Good | Yes | 13+ | ~200ms | ~$0.05-0.10 |
| **WellSaid** | Very good | No (actor voices) | English | ~300ms | Custom pricing |
| **Voicebox** | Good | Yes (local) | 2+ | Local | Free (open 来源) |

### Choosing a Voice 工具

```
Need voiceover for ads?
├── Need to clone a specific brand voice?
│   ├── Best quality → ElevenLabs
│   ├── Enterprise/on-premise → Resemble AI
│   └── Budget-friendly → Fish Audio, PlayHT
├── Need multilingual (same ad, many languages)?
│   ├── Most languages → PlayHT (140+)
│   └── Best quality → ElevenLabs (29+)
├── Need free / open source / local?
│   └── Voicebox (MIT, runs on your machine)
├── Need cheap, fast, good-enough?
│   └── OpenAI TTS ($0.015/min)
├── Need commercially-safe licensing?
│   └── WellSaid Labs (actor-compensated voices)
└── Need real-time/interactive?
    └── Cartesia Sonic (40ms TTFA)
```

### 工作流: Voice + 视频

```
1. Write ad script (use ad-creative skill for copy)
2. Generate voiceover with ElevenLabs/OpenAI TTS
3. Generate or render video:
   a. Silent video from Runway/Remotion → layer voice track
   b. Or use Veo/Sora/Seedance with native audio (skip separate VO)
4. Combine with ffmpeg if layering separately:
   ffmpeg -i video.mp4 -i voiceover.mp3 -c:v copy -c:a aac output.mp4
5. Generate variations (different scripts, voices, or languages)
```

---

## Code-Based 视频: Remotion

For templated, data-driven 视频 ads at scale, Remotion is the best option. Unlike AI 视频 generators that produce unique 视频 from prompts, Remotion uses React code to render deterministic, brand-perfect 视频 from templates and data.

**Best for:** Templated ad variations, personalized 视频, brand-consistent production
**Stack:** React + TypeScript
**Pricing:** Free for individuals/small teams; commercial license required for 4+ employees
**Docs:** [remotion.dev](https://www.remotion.dev/)

### Why Remotion for Ads

| AI 视频 Generators | Remotion |
|---------------------|----------|
| Unique output each time | Deterministic, pixel-perfect |
| Prompt-based, less control | Full code control over every frame |
| Hard to match brand exactly | Exact brand colors, fonts, spacing |
| One-at-a-time generation | Batch render hundreds from data |
| No dynamic data insertion | Personalize with names, prices, stats |

### Ad Creative Use Cases

**1. Dynamic 产品 ads**
Feed a JSON array of products and render a unique 视频 ad for each:
```tsx
// Simplified Remotion component for product ads
export const ProductAd: React.FC<{
  productName: string;
  price: string;
  imageUrl: string;
  tagline: string;
}> = ({productName, price, imageUrl, tagline}) => {
  return (
    <AbsoluteFill style={{backgroundColor: '#fff'}}>
      <Img src={imageUrl} style={{width: 400, height: 400}} />
      <h1>{productName}</h1>
      <p>{tagline}</p>
      <div className="price">{price}</div>
      <div className="cta">Shop Now</div>
    </AbsoluteFill>
  );
};
```

**2. A/B test 视频 variations**
Render the same template with different headlines, CTAs, or color schemes:
```tsx
const variations = [
  {headline: "Save 50% Today", cta: "Get the Deal", theme: "urgent"},
  {headline: "Join 10K+ Teams", cta: "Start Free", theme: "social-proof"},
  {headline: "Built for Speed", cta: "Try It Now", theme: "benefit"},
];
// Render all variations programmatically
```

**3. Personalized outreach videos**
Generate videos addressing prospects by name for cold outreach or sales.

**4. Social ad batch production**
Render the same content across different aspect ratios:
- 1:1 for feed
- 9:16 for Stories/Reels
- 16:9 for YouTube

### Remotion 工作流 for Ad Creative

```
1. Design template in React (or use AI to generate the component)
2. Define data schema (products, headlines, CTAs, images)
3. Feed data array into template
4. Batch render all variations
5. Upload to ad platform
```

### Getting Started

```bash
# Create a new Remotion project
npx create-video@latest

# Render a single video
npx remotion render src/index.ts MyComposition out/video.mp4

# Batch render from data
npx remotion render src/index.ts MyComposition --props='{"data": [...]}'
```

---

## Choosing the Right 工具

### Decision Tree

```
Need video ads?
├── Templated, data-driven (same structure, different data)
│   └── Use Remotion
├── Unique creative from prompts (exploratory)
│   ├── Need dialogue/voiceover? → Sora 2, Veo 3.1, Kling 2.6, Seedance 2.0
│   ├── Need consistency across scenes? → Runway Gen-4
│   ├── Need vertical social video? → Veo 3.1 (native 9:16)
│   ├── Need high volume at low cost? → Seedance 2.0
│   └── Need cinematic camera work? → Higgsfield, Kling
└── Both → Use AI gen for hero creative, Remotion for variations

Need image ads?
├── Need text/headlines in image? → Ideogram
├── Need product consistency across variations? → Flux (multi-ref)
├── Need quick iterations on existing images? → Nano Banana Pro
├── Need highest visual quality? → Flux Pro, Midjourney
└── Need high volume at low cost? → Flux Klein, Nano Banana
```

### Cost Comparison for 100 Ad Variations

| Approach | Tool | Approximate Cost |
|----------|------|-----------------|
| 100 static images | Nano Banana Pro | ~$4-24 |
| 100 static images | Flux Dev | ~$1-2 |
| 100 static images | Ideogram API | ~$6 |
| 100 × 15-sec videos | Veo 3.1 Fast | ~$225 |
| 100 × 15-sec videos | Remotion (templated) | ~$0 (self-hosted render) |
| 10 hero videos + 90 templated | Veo + Remotion | ~$22 + render time |

### Recommended 工作流 for Scaled Ad Production

1. **Generate hero creative** with AI (Nano Banana, Flux, Veo) — high-质量, exploratory
2. **Build templates** in Remotion based on winning creative patterns
3. **Batch produce variations** with Remotion using data (products, headlines, CTAs)
4. **Iterate** — use AI tools for new angles, Remotion for scale

This hybrid approach gives you the creative exploration of AI generators and the consistency and scale of code-based rendering.

---

## 平台-Specific Image Specs

When generating images for ads, request the correct dimensions:

| 平台 | Placement | Aspect Ratio | Recommended Size |
|----------|-----------|-------------|-----------------|
| Meta Feed | Single image | 1:1 | 1080x1080 |
| Meta Stories/Reels | Vertical | 9:16 | 1080x1920 |
| Meta Carousel | Square | 1:1 | 1080x1080 |
| Google 展示 | Landscape | 1.91:1 | 1200x628 |
| Google 展示 | Square | 1:1 | 1200x1200 |
| LinkedIn Feed | Landscape | 1.91:1 | 1200x627 |
| LinkedIn Feed | Square | 1:1 | 1200x1200 |
| TikTok Feed | Vertical | 9:16 | 1080x1920 |
| Twitter/X Feed | Landscape | 16:9 | 1200x675 |
| Twitter/X Card | Landscape | 1.91:1 | 800x418 |

Include these dimensions in your generation prompts to avoid needing to crop or resize.
