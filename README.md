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
--- Cutline ---
1. Generate video/audio clips with recap
2. User can click a button to "play from here" or open the page to revisit the referenced moment instantly
3. User can read a character glossary personalized up and to point that the user has consumed
4. User can search within a given chapter/movie/show
5. Users can read/listen/watch recaps in their preferred language
6. User can create a shareable link to a recap the spoiler boundary

#### Non-Functional Requirements

#### Core Entities

#### High Level Design

#### Low Level Design

# User Experience

#### Intended Audience
* VOD viewers who took a break from binging
* Audiobook Listeners
* Manga/Comic readers

#### User Pains

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
