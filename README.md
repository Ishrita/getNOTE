# [getNOTE]

> Bee listens to your lecture. We turn it into notes, flashcards, and quizzes, so you can focus on learning instead of writing.

Built for the **Build, Ship, Shape: Amazon Developer Hackathon** (Bee track).

---

## The problem

In class, students have to listen and write at the same time, and one of them suffers. Raw transcripts don't fix this: they are long, full of filler, and mix key points with chatter. **[Project Name]** closes the gap between "Bee heard it" and "I can revise from it."

## What it does

- **Cleans** lecture transcripts (removes filler, repetition, off-topic talk)
- **Segments** the lecture by topic
- **Extracts** key terms, definitions, formulas, and examples
- **Writes structured notes** (headings, bullets, short summary)
- **Generates flashcards and a quick quiz** for revision

Notes are written from topic *segments*, not isolated keywords. Keywords decide what matters; the LLM preserves the meaning.

## How it works

```
Bee wearable → Bee CLI / MCP export → clean → topic segmentation
            → key-term extraction → LLM note generation → flashcards + quiz → web UI
```

1. **Input:** conversation/lecture data from Bee (via Bee CLI or MCP) or a sample transcript.
2. **Processing:** cleaning, topic segmentation, and key-term ranking.
3. **Generation:** an LLM writes notes per segment, then creates flashcards and quiz questions.
4. **UI:** transcript on one side, notes building up on the other.

## Tech stack

- Python, FastAPI
- React (or plain HTML/JS)
- Amazon Bedrock (LLM)
- Bee CLI / MCP

## Getting started

### Prerequisites

- Python 3.10+
- Node.js 18+ (if using a React frontend)
- AWS credentials with Bedrock access (or your LLM API key)
- *(Optional)* A Bee device and the Bee CLI

### Installation

```bash
git clone https://github.com/[your-username]/[repo-name].git
cd [repo-name]

# backend
pip install -r requirements.txt

# frontend (if applicable)
cd frontend && npm install
```

Export conversations and point the app at the exported Markdown files (see `.env` / config).

**Without a device (demo mode):** use the sample lecture transcripts in `/samples`. The rest of the pipeline is identical.

> Be honest here about which mode your demo uses.

## Project structure

```
.
├── app/                 # backend (pipeline, API)
│   ├── clean.py         # transcript cleaning
│   ├── segment.py       # topic segmentation
│   ├── notes.py         # note generation
│   └── flashcards.py    # flashcards + quiz
├── frontend/            # web UI
├── samples/             # sample lecture transcripts
├── requirements.txt
└── README.md
```

## Challenges

- Keeping meaning while cutting words (moved from keyword-only to segment-level summarization)
- Finding clean topic boundaries in repetitive spoken language
- Handling technical terms and formulas in transcripts
- Scoping a working core flow into a tight timeline

## Roadmap

- Subject-specific note templates (math, biology, history)
- Timestamps linking notes back to the lecture
- "Mark as important" signal during class
- Hindi-English mixed-language support
- Export to PDF and Notion

## Privacy

Recording a class may require permission from the teacher or institution. Bee discards audio after transcription; this project works with text only.


## License

[MIT / your choice]
