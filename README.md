# Amazon Fulfillment Center: Workforce Sentiment & Root Cause Analysis

*Role:* Data Analyst (Amazon Operational Strategy & People Analytics Externship Project)

## Overview

This project analyzes employee sentiment from an Amazon Fulfillment Center using publicly available Glassdoor reviews and YouTube employee testimonials. The goal was to identify which workforce segment is experiencing the most friction, uncover the root causes behind it, and design a low-cost, measurable intervention to test before any large-scale rollout.

The analysis follows a full pipeline: raw text → cleaned data → sentiment scoring → thematic tagging → workforce segmentation → root cause analysis → intervention design → executive presentation.

## Dataset

- *Sources:* Glassdoor employee reviews, YouTube employee testimonials/comments
- *Combined dataset:* 150 rows across both platforms
- *Key fields:* platform, cleaned_text, sentiment_polarity, sentiment_subjectivity, sentiment_label, Theme, Segment, employee_status, employee_job_title

## Pipeline

1. *Data collection* - Manually gathered Glassdoor reviews and YouTube comments mentioning working conditions at Amazon fulfillment centers.
2. *Text cleaning* - Lowercased text, removed punctuation, filtered stopwords (NLTK), normalized Unicode characters.
3. *Keyword & n-gram frequency analysis*: Identified the most common words and phrases across reviews to surface recurring themes.
4. *Sentiment scoring* - Used TextBlob to score each review's polarity (positive/negative) and subjectivity.
5. *Thematic tagging* - Used Gemini for an initial pass at theme generation, then manually verified and corrected each tag for accuracy.
6. *Workforce segmentation* - Grouped reviews by employee_status × employee_job_title (e.g., Full-Time Warehouse Associates, Part-Time Warehouse Associates, Management & Specialized Roles, Contract & Temporary Workers).
7. *Priority scoring* - Ranked segments using Impact × Severity × Size to identify where an intervention would have the greatest effect.
8. *Root cause analysis* - Applied the 5 Whys framework and built a root cause tree (Claude.ai-assisted) to trace surface complaints back to underlying drivers.
9. *Friction mapping* - Mapped each friction point across Segment, Experience, Friction Point, Business Impact, and supporting employee quotes.
10. *Intervention design* - Framed the problem ("[Segment] is experiencing [challenge], which leads to [business risk]"), posed a "How Might We" question, and designed a People/Process/Technology (PPT) pilot intervention.

## Key Findings

| Segment | Mentions | Negative Sentiment |
|---|---|---|
| *Full-Time Warehouse Associates* | *88* | *15% (highest)* |
| Part-Time Warehouse Associates | 23 | *9%* |
| Management & Specialized Roles | 18 | *11%* |
| Contract & Temporary Workers | 9 | *0%* |

- *46* pay/overtime-related mentions: the strongest friction signal in the dataset
- *Priority Score:(Impact 5 × Severity 4 × Size 5) * 100 - Full-Time Warehouse Associates rank highest across all three factors
- Representative quote: "I worked 60 hours in that warehouse and barely made $1,000."(YouTube reveiw)
- Contract & Temporary Workers show 0% negative sentiment, likely reflecting limited review volume for this segment rather than genuinely higher satisfaction.

*Problem Statement:* Full-Time Warehouse Associates are experiencing overtime pressure because base pay does not meet their income needs, increasing burnout and turnover risk.

## Recommendation

*Pilot an opt-in recovery-time option for one Full-Time Associate team.*

- *People:* Learning Ambassador leads rollout; employee feedback drives iteration
- *Process:* Opt-in recovery time, weekly check-ins, single-team pilot (4–8 weeks)
- *Technology:* Uses Amazon's existing scheduling system, no new software cost
- *Success signals:* Recovery-time take-up rate, weekly employee feedback

This approach was informed by a real, sourced case study (a fulfillment operation that reduced overtime by 32% and turnover by 24% through employee-driven scheduling flexibility [myshyft.com](https://www.myshyft.com)), adapted to use only tools already available at no additional cost.

## Repository Structure

```
notebooks/      # Google Colab notebooks: cleaning, sentiment, theme tagging, segmentation
data/           # CSV outputs at each pipeline stage
visuals/        # Charts, friction flow diagrams, word clouds
presentation/   # Final 5-slide executive deck (PPTX/PDF)
README.md
```

## Tools Used

- *Python*: (Pandas, NLTK, TextBlob, Matplotlib, WordCloud) — Google Colab
- *Gemini*: initial thematic tagging
- *Claude.ai*: root cause tree, friction map visualization
- *Canva AI*: final presentation design
- *Loom*: recorded walkthrough of findings and recommendation

## Author

*Jemilah Alao* - Data Analyst transitioning from an Animal Science and farm operations background into tech.
[LinkedIn](https://www.linkedin.com/in/jemilah-alao-8a684528a) · alao.jemilah@gmail.com
