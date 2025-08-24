# recapkit
Spoiler-safe recaps &amp; character Q&amp;A from captions and media transformed into text


# System Design

#### Functional Requirements
1. Users should be able to get a spoiler-free recaps strictly from segments at or before the user's last progress
2. As a viewer, I can request a recap that only includes events up to where I stopped (episode time / audiobook time / manga page), so nothing ahead is spoiled
3. User can choose a 30 second, 60 second, or 120 second recap and get a summary that fits that budget
4. User can ask targeted questions about a character or plot and get answers with citations to the exact episode timestamp, chapter timestamp or page
5. Ingest video captions by way of WebVTT (Web Video Text Tracks) or SRT (Secure Reliable Transport), audiobook text as EPUB/TXT/JSON, and PDF/CBZ (Comic Book Zip)
6. User can flag a recap as incorrect or containing spoilers and optionally post a note so it can be fixed

--- Cutline (later priorities) ---
1. Generate video/audio clips with recap
2. User can click a button to "play from here" or open the page to revisit the referenced moment instantly
3. User can read a character glossary personalized up and to point that the user has consumed
4. User can search within a given chapter/movie/show
5. Users can read/listen/watch recaps in their preferred language
6. User can create a shareable link to a recap the spoiler boundary
7. Users can personalize the tone, voice, language and more of the recap video/audio

#### Non-Functional Requirements
1. The system should generate recap text in under 30 seconds
2. The system should generate character/plot answers in sub 7 seconds
3. The system should return in-chapter/in-episode search results in under 500 ms
4. The system should support 1 million MAU and handle 100,000 concurrent users
5. The system should ingest Media Assets within 30 minutes after release of the latest chapter/episode/
6. The system is read heavy, and thus needs to be able to support high read throughput. The system should handle spikes around events like new seasons, new releases, etc. expect 100:1 read:writes and 1000:1 for spikes. 
7. The system should only accept public domain or user-provided content. DMCA takedown should occur within 3 days of receiving the request.
8. The system should cache popular recaps with TTL
9. The system should limit requests per minute per user to 100 (10 per day per user for beta/MVP) and limit to 1000 per minute per IP

--- Cutline (later priorities) ---
1. The system should generate recap videos in under two minutes
2. The system should integrate with major players like YouTube, Netflix, Amazon Prime, Viz, Audible, etc and open the media for "play from here" or viewing referenced moment in under 250 ms
3. 
4. The system should be GDPR or CCPA compliant with user data deletion capabilities
5. The system should generate the consistent base recap given the same progress points (personalization layer separated and a black box for now)

#### Core Entities
User, Recap, Title, Media, Query, Response, Citation, Feedback

| Table       | Table Examp | Tablee      | Table Stub  |
| ----------- | ----------- | ----------- | ----------- |
| Header      | Title       | Header      | Title       |
| Paragraph   | Text        | Paragraph   | Text        |

#### APIs
* POST /api/v1/media/ingest
* GET /api/v1/media/jobs/{jobId}/status
* POST /api/v1/recaps/generate
* POST /api/v1/queries
* PUT /api/v1/progress
* GET /api/v1/progress/{mediaId}
* GET /api/v1/search
* POST /api/v1/feedback
* ws://api/v1/progress/stream

Use REST for majority of the web layer's CRUD operations, GraphQL for complex nested queries related to character relationships or multi-media queries, try to figure out a proof of concept for dynamically updating user progress (off top of head means it requires API integration and OAuth with each service that contains media; for MVP use REST for users to simply select media title, select start point and last progress point but future likely WebSocket or Event-driven) and use RPC for internal service to service communication likely the small language model service and the ingestion pipeline.

#### High Level Design

#### Low Level Design

#### Database Models

#### Service Interface Data Modeling

# User Experience

#### Intended Audience
* VOD viewers who took a break from binging
* Audiobook Listeners
* Manga/Comic readers
* Narrative/Serial podcast listners

#### User Pains
* Hard to remember narrative state across time gaps (in between seasons, releases, sequels, etc)
* Trying to gain information without spoilers
* Media progress is fragmented across streaming/VOD platforms, audio platforms, and web readers
* 

#### Hypothesis
* Should lead to more engagement from watchers, listeners and readers as they are more likely to not give up on a series if they receive recaps without spoilers

#### Current Recap Sources
* Social media like YouTube, TikTok
* Streaming service curated recap reels between seasons (but not every title has a recap)
* 

# Product

#### Product Vision
Think DBZ-esque, "previously on..." for any chapter, episode, movie, or piece of media in a series

#### Product Areas
* Engagement
* Discovery
* Personalization
* Social Sharing

#### BRD
