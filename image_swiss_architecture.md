## ImageSwiss Architecture & Roadmap

### 1. Architecture Overview

```mermaid
flowchart LR
    subgraph Frontend
        UI[Drag & Drop Uploader + Checklist]
        TokenUI[Token Balance & Cost Preview]
        Download[Download Processed Images / Zip]
    end

    subgraph Backend
        API[REST API / GraphQL]
        Auth[User Auth & Tokens]
        JobQueue[Job Queue / Batch Processing]
        FastOps[Fast Local Ops: Resize, Convert, Compress]
        AIQueue[AI Task Processor]
    end

    subgraph AI
        AIWorker[AI Operations: Background Removal, OCR, Filters]
        OpenAI[OpenAI / ChatGPT API or Local Model]
    end

    subgraph Storage
        TempStorage[S3 / S3-Compatible Temp Storage]
        ProcessedStorage[Processed Images Storage]
    end

    subgraph Payment
        Stripe[Stripe Payments for Token Packs]
    end

    UI --> API
    TokenUI --> API
    API --> Auth
    API --> JobQueue
    JobQueue --> FastOps
    JobQueue --> AIQueue
    AIQueue --> AIWorker
    AIWorker --> OpenAI
    FastOps --> ProcessedStorage
    AIWorker --> ProcessedStorage
    ProcessedStorage --> Download
    API --> Stripe
```

### 2. Roadmap (Solo Dev / Part-Time)

**Phase 0: Planning & Validation (Week 1–2)**
- Finalize PRD & feature checklist
- Landing page / email capture
- Tech stack selection
- Draft token model

**Phase 1: Core Fast Operations (Week 3–6)**
- Upload & download flow
- Fast Local Ops: Resize, Format Conversion, Compress
- Batch upload support
- Zip download
- Internal testing

**Phase 2: Token System (Week 7–9)**
- User auth (email / OAuth)
- Token accounting & cost preview
- Stripe integration
- Token balance UI
- Edge cases handling

**Phase 3: AI Trial Operations (Week 10–12)**
- AI Ops: Background removal, OCR, filters
- Fast trial: high token, quick
- Slow batch: low token, asynchronous
- Queue system & notifications

**Phase 4: MVP Polishing & Launch (Week 13–16)**
- UI/UX polish, progress bars, job status
- Email notifications for batch jobs
- Error logging & monitoring
- Beta launch (10–20 users)
- Collect feedback & fix issues

**Phase 5: Post-MVP / Optional Features (Month 5–6)**
- Developer API
- Zapier / Make integrations
- Analytics dashboard
- Advanced AI-powered utilities
- Marketing ramp-up: blog posts, SEO, community launch

