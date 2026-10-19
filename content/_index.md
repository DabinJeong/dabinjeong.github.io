---
title: ''
summary: ''
date: 2022-10-24
type: landing

sections:
  # ── Hero + About me + Experience + News + Education ───────────────────────
  - block: markdown
    id: profile
    content:
      title: ''
      text: |-
        <div class="dj-layout">
        <div class="dj-hero">
        <img class="dj-photo" src="/images/profile.png" alt="Dabin Jeong" width="160" height="160">
        <div class="dj-hero-text">
        <h1>Dabin Jeong</h1>
        <p class="dj-role">AI for Life Science Researcher</p>
        <ul class="dj-contact">
        <li><img class="dj-ico-img" src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/739ab583-004d-484e-b944-d0a23121ad74/location.jpg" alt="" width="20" height="20" onerror="this.style.visibility='hidden'"><span>Wellcome Sanger Institute, Cambridge, UK</span></li>
        <li><span class="dj-ico">✉️</span><a href="mailto:dj16@sanger.ac.uk">dj16@sanger.ac.uk</a></li>
        <li><img class="dj-ico-img" src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/495c8ba1-627e-4adb-835e-d217b5fdea8e/github.png" alt="" width="20" height="20" onerror="this.style.visibility='hidden'"><a href="https://github.com/DabinJeong">GitHub</a></li>
        <li><img class="dj-ico-img" src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/b64adb4e-8e3d-4847-8234-dec766f2308e/square-linkedin-logo-isolated-white-background_469489-892.avif" alt="" width="20" height="20" onerror="this.style.visibility='hidden'"><a href="http://www.linkedin.com/in/dabin-jeong-421914261/">LinkedIn</a></li>
        <li><img class="dj-ico-img" src="https://s3-us-west-2.amazonaws.com/public.notion-static.com/a5a8f6e5-9403-4434-8bcd-7ce2398e7908/Google_Scholar_logo.svg.png" alt="" width="20" height="20" onerror="this.style.visibility='hidden'"><a href="https://scholar.google.com/citations?hl=en&user=Ne2p354AAAAJ">Google Scholar</a></li>
        </ul>
        </div>
        </div>

        <div class="dj-main">

        ## About me {#about}

        I am an AI for Life Science researcher at the [Lotfollahi Lab](https://www.sanger.ac.uk/group/lotfollahi-group/), Wellcome Sanger Institute, working at the intersection of machine learning and biomedical science.

        I see myself as a problem finder as much as a problem solver. My background in bioinformatics and biochemistry leads me to look for gaps where existing computational approaches fall short. Rather than simply applying established AI frameworks to biology, I focus on identifying under-explored problems in the domain and developing novel solutions to address the problems. I translate the complexity of biological and medical questions into well-defined computational problems, then build the models needed to solve them.

        <div class="dj-cols">
        <div>

        ### 💡 Research Interest

        - Multi-modal learning of biomedical images and spatial transcriptomics
        - Regulatory DNA sequence generation
        - Temporal cell dynamics modeling

        </div>
        <div>

        ### 🚩 Research Vision

        > *“What I cannot create, I do not understand”* — Richard Feynman

        I was drawn to computational biology by the idea that DNA is the ultimate code: a sequence in which both code and the codebook are deeply entangled. My research ambition is to build a program that can simulate biological systems from DNA sequence.

        </div>
        </div>

        ## 🔥 News {#news}

        <div class="dj-emoji-list">

        - 🎉 **Sep 2026** · LocoGen, a locality-aware generative model for designing regulatory DNA, was accepted to NeurIPS 2026.
        - 🎉 **Jul 2026** · Selected as one of 500 participants from over 6,000 applicants in the Anthropic × Gladstone Claude Life Sciences Hackathon, where I built a generative model that infers missing cell states across time points ([LinkedIn post](https://www.linkedin.com/posts/dabin-jeong-421914261_claudelifesciencehackathon-share-7485488602135642112-kiKJ/)).
        - 🎉 **Jun 2026** · SIGMMA was accepted to the ICML FM4LS/SD4H workshop; a journal version is in preparation ([manuscript](https://icml.cc/virtual/2026/72055)).
        - 🎉 **Oct 2024** · Joined the Wellcome Sanger Institute.

        </div>

        ## 💼 Professional Experience {#experience}

        **Senior Data Scientist** · Wellcome Sanger Institute, UK · *Oct 2024 – present*

        - Led **SIGMMA**, a hierarchical contrastive learning framework aligning H&E histopathology with spatial transcriptomics ([ICML 2026 workshop paper](https://openreview.net/pdf?id=npTFOLkCDf); journal version in preparation)
        - Led **LocoGen**, a generative framework for de novo regulatory DNA design that uses property-guided generation for out-of-distribution objectives in a lab-in-the-loop cycle (NeurIPS 2026)

        **Research Intern** · LG AI Research, Korea · *Jan – Apr 2024*

        - Contributed to **ExaonePath**, a self-supervised foundation model for H&E histopathology images ([press](https://press.aboutamazon.com/2024/12/lg-ai-research-develops-ai-model-on-aws-for-rapid-cancer-diagnosis))
        - Built a scalable, reproducible multi-omics preprocessing pipeline

        ## 🧬 Projects {#projects}

        <div class="dj-project-grid">

        <div class="dj-project-card">
          <h4>🔬 Spatial transcriptomics × histopathology</h4>
          <ul>
            <li><strong>SIGMMA</strong> · <em>Lead · 2025 – present</em><br>
              Hierarchical contrastive learning aligning H&amp;E histopathology with spatial transcriptomics.<br>
              <a href="https://icml.cc/virtual/2026/72055">ICML 2026 workshop</a> · journal version in preparation</li>
            <li><strong>ExaonePath</strong> · <em>Contributor · 2024, LG AI Research</em><br>
              Self-supervised foundation model for H&amp;E histopathology images.<br>
              <a href="https://press.aboutamazon.com/2024/12/lg-ai-research-develops-ai-model-on-aws-for-rapid-cancer-diagnosis">press</a></li>
          </ul>
        </div>

        <div class="dj-project-card">
          <h4>🧬 Regulatory DNA generation</h4>
          <ul>
            <li><strong>LocoGen</strong> · <em>Lead · 2025 – present</em><br>
              Generative framework for de novo regulatory DNA design that uses property-guided generation for out-of-distribution objectives in a lab-in-the-loop cycle.<br>
              NeurIPS 2026</li>
          </ul>
        </div>

        <div class="dj-project-card">
          <h4>⏱️ Temporal cell dynamics</h4>
          <ul>
            <li><strong>Cell-state inference across time</strong> · <em>2026, Anthropic × Gladstone Hackathon</em><br>
              A generative model that infers missing cell states across time points.<br>
              <a href="https://www.linkedin.com/posts/dabin-jeong-421914261_claudelifesciencehackathon-share-7485488602135642112-kiKJ/">LinkedIn post</a></li>
          </ul>
        </div>

        <div class="dj-project-card">
          <h4>🧪 Multi-omics biomarker discovery</h4>
          <ul>
            <li><strong>GOAT</strong> · <em>Lead · PhD</em><br>
              Graph neural network for multi-omics biomarker discovery in eosinophilic asthma.<br>
              <a href="https://academic.oup.com/bioinformatics/article/39/10/btad582/7280697">Bioinformatics, 2023</a></li>
            <li><strong>VWA5A as a biomarker in breast cancer</strong> · <em>Co-lead · PhD</em><br>
              Machine-learning-based protein prioritization identifying VWA5A as a prognostic marker for breast-cancer metastasis.<br>
              <a href="https://www.nature.com/articles/s41598-024-53015-1">Scientific Reports, 2024</a></li>
            <li><strong>Patent (Korea)</strong> · <em>Inventor</em><br>
              Multi-omics biomarker discovery method, registered through the Korean Intellectual Property Office.<br>
              <a href="https://www.kipris.or.kr/khome/detail/newWindow.do">KIPRIS</a></li>
          </ul>
        </div>

        </div>

        ## 🎓 Education {#education}

        **Ph.D., Interdisciplinary Program of Bioinformatics** · Seoul National University, Korea · *Sep 2018 – Aug 2024*

        - Thesis: *Computational modeling of molecular interactions for biomarker discovery using single/multi-omics data*
        - 3 first-authored and 10 co-authored papers
        - Developed **GOAT**, a graph neural network for multi-omics biomarker discovery in eosinophilic asthma ([Bioinformatics, 2023](https://academic.oup.com/bioinformatics/article/39/10/btad582/7280697))
        - Developed RNA-seq quantification and normalization pipelines for ICGC-ARGO

        **B.S., Biochemistry** · Yonsei University, Korea · *Mar 2013 – Aug 2018*

        </div>
        </div>

  # ── Skills, Awards ─────────────────────────────────────────────────────────
  - block: markdown
    id: more
    content:
      title: ''
      text: |-
        ## Technical Skills {#skills}

        - **Programming** · Python, R, Shell, LaTeX
        - **ML / Deep Learning** · PyTorch, PyTorch Geometric, DGL, scikit-learn
        - **Workflow & Reproducibility** · Nextflow, Snakemake, Docker, Git

        ## Awards & Achievements {#awards}

        <div class="dj-emoji-list">

        - 🏆 **Invited talk (2023)** · National Heart & Lung Institute, Imperial College London (host: Prof. Kian Fan Chung) — *Deep graph attention for multi-omics network biomarkers in eosinophilic asthma*
        - 🏆 **National Excellence Scholarship (2016)** · Natural Sciences and Engineering; sole recipient in the department

        </div>

  # ── Photo ──────────────────────────────────────────────────────────────────
  - block: markdown
    id: photo
    content:
      title: ''
      text: |-
        ## 📷 Photo {#photo}

        <div class="dj-photo-grid">
        <!-- Add photos here, e.g.:
        <figure><img src="/photos/example.jpg" alt="caption"><figcaption>caption</figcaption></figure>
        -->
        </div>

        <p class="dj-soon">Photos coming soon.</p>
---
