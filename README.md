# Watcha Finder

A Claude Code skill for discovering and evaluating AI products using the [watcha.cn](https://watcha.cn) platform API.

## What It Does

Watcha Finder helps you find AI products that genuinely fit your needs — not just the most popular ones. It:

- **Searches watcha.cn's 1000+ product database** with smart fallback strategies (the API isn't fuzzy search)
- **Reads actual user reviews** to understand community sentiment beyond just scores
- **Distinguishes popularity from quality** — review/reply counts show hype, not necessarily value
- **Cross-references with web sources** to avoid misjudgments from low community activity
- **Provides nuanced recommendations** with clear reasoning about trade-offs

## Key Features

- Multi-strategy search (text queries, category filtering, Chinese/English keywords)
- Deep-dive analysis with review text extraction
- Score reliability assessment (flags products with too few reviews)
- Dark horse discovery (finds lesser-known but high-quality products)
- China availability filtering
- Platform/pricing/feature comparison

## Installation

This is a Claude Code skill. To use it:

1. Copy the `watcha-finder/` directory to your Claude Code skills location
2. The skill will automatically be available when you ask about AI products

## Usage Examples

```
帮我找一个好用的AI编程工具，最好支持本地运行
```

```
I need an AI video creation tool that works in China, what are my options?
```

```
最近有什么值得关注的AI产品？不要只看热门的
```

## How It Works

The skill uses the watcha.cn API to:

1. **Search broadly** — tries multiple query strategies since search is exact-match
2. **Shortlist candidates** — picks 3-5 products based on relevance and data quality
3. **Deep-dive** — fetches product details, reviews (up to 20), and community posts
4. **Web search** — supplements watcha data with external perspectives
5. **Synthesize** — presents findings with nuanced quality assessment

## API Reference

The skill accesses these watcha.cn endpoints:

- `POST /api/v2/search/general` — product search with category/tag filtering
- `GET /api/v2/products/{id}` — product details
- `GET /api/v2/products/{id}/reviews` — user reviews
- `GET /api/v2/products/{id}/posts` — community discussions

## Categories Supported

- 通用助手 (General Assistant)
- 编程开发 (Coding/Dev)
- 图像生成 (Image Generation)
- 视频创作 (Video Creation)
- 音频处理 (Audio Processing)
- 写作辅助 (Writing)
- 知识管理 (Knowledge Management)
- 智能搜索 (Smart Search)
- Agent 构建 (Agent Building)
- 效率工具 (Productivity)
- And more...

## Development

### Project Structure

```
findai/
└── watcha-finder/           # The skill
    ├── SKILL.md            # Skill instructions
    └── evals/
        └── evals.json      # Test cases
```

## Limitations

- Search API is exact-match, not fuzzy (skill handles this with multiple query strategies)
- Review/reply counts indicate popularity, not quality (skill explicitly accounts for this)
- Scores with <10 reviews are unreliable (skill flags these)
- Products with low watcha activity may still be excellent (skill supplements with web search)

## License

MIT

## Credits

Built using the [watcha.cn](https://watcha.cn) API — a Chinese AI product discovery platform with community reviews and ratings.
