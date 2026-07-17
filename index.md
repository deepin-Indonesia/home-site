---
layout: default
title: Beranda
permalink: /
---

<!-- Hero Section with YouTube Video -->
<section class="hero">
  <div class="hero-overlay"></div>
  <div class="hero-content container">
    <div class="hero-text">
      <img src="{{ '/assets/images/deepin-id.png' | relative_url }}" alt="deepin Indonesia" class="hero-logo-text">
      <p class="hero-description">
        Selamat datang di komunitas <strong>deepin Indonesia</strong> — tempat berkumpulnya pengguna dan pengembang deepin di tanah air. 
        Mari bersama menjelajahi sistem operasi Linux yang indah, modern, dan mudah digunakan.
      </p>
      <div class="hero-actions">
        <a href="/download/" class="btn btn-primary">
          <i class="fas fa-download"></i> Download deepin
        </a>
        <a href="/gabung-komunitas/" class="btn btn-outline">
          <i class="fas fa-users"></i> Gabung Komunitas
        </a>
      </div>
    </div>
    <div class="hero-video">
      <div class="video-wrapper">
        <iframe
          src="https://www.youtube-nocookie.com/embed/w0fyT59D6nw?rel=0&modestbranding=1"
          title="deepin 25 Video"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          allowfullscreen>
        </iframe>
      </div>
      <p class="video-caption">Tonton pengenalan <strong>deepin 25</strong> — Lebih indah, lebih cepat, lebih andal.</p>
    </div>
  </div>
</section>

<!-- Mengapa deepin Indonesia Section -->
<section class="why-deepin-id">
  <div class="container">
    <div class="section-header">
      <h2>Mengapa deepin Indonesia?</h2>
      <p class="section-subtitle">
        deepin Indonesia adalah komunitas resmi yang didedikasikan untuk mendukung pengguna deepin di Indonesia. 
        Kami menyediakan panduan, diskusi, dan event seputar deepin dalam Bahasa Indonesia.
      </p>
    </div>
    <div class="features-grid">
      <div class="feature-item">
        <div class="feature-icon">
          <i class="fas fa-language"></i>
        </div>
        <h3>Bahasa Indonesia</h3>
        <p>Konten, diskusi, dan dokumentasi dalam Bahasa Indonesia, memudahkan pengguna lokal memahami deepin.</p>
      </div>
      <div class="feature-item">
        <div class="feature-icon">
          <i class="fas fa-comments"></i>
        </div>
        <h3>Komunitas Aktif</h3>
        <p>Diskusi hangat dan saling membantu di grup Telegram. Dari pemula hingga expert, semua diterima.</p>
      </div>
      <div class="feature-item">
        <div class="feature-icon">
          <i class="fas fa-calendar-alt"></i>
        </div>
        <h3>Event & Workshop</h3>
        <p>Meetup, workshop instalasi, dan kontribusi open-source secara berkala untuk anggota komunitas.</p>
      </div>
    </div>
  </div>
</section>

<!-- Why deepin Section -->
{% include why-deepin.html %}

<!-- Community Lead Section -->
<section class="community-lead">
  <div class="container">
    <div class="lead-card">
      <div class="lead-avatar">
        <img src="{{ '/assets/images/zaky-nr.jpg' | relative_url }}" alt="Zaky NR" class="lead-avatar-img">
      </div>
      <div class="lead-info">
        <span class="lead-badge">Official deepin Global Ambassador for Indonesia</span>
        <h2>Zaky NR</h2>
        <p class="lead-title">Lead, deepin Indonesia Community</p>
        <p class="lead-bio">
          Memimpin dan menggerakkan komunitas deepin di Indonesia. Berdedikasi untuk memperkenalkan 
          deepin ke lebih banyak pengguna di tanah air melalui edukasi, event, dan kolaborasi.
        </p>
        <div class="lead-actions">
          <a href="https://zaky.siberin.id/" target="_blank" rel="noopener" class="btn btn-sm btn-primary">
            <i class="fas fa-globe"></i> Website
          </a>
          <a href="https://github.com/JackTekno" target="_blank" rel="noopener" class="btn btn-sm btn-github">
            <i class="fab fa-github"></i> GitHub
          </a>
          <a href="https://zaky.siberin.id/#kontak" target="_blank" rel="noopener" class="btn btn-sm btn-outline-lead">
            <i class="fas fa-envelope"></i> Kontak
          </a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- Call to Action -->
<section class="cta">
  <div class="container">
    <div class="cta-content">
      <h2>Siap mencoba deepin?</h2>
      <p>Bergabunglah dengan ratusan pengguna deepin lainnya di Indonesia. Mulai perjalanan Linux Anda hari ini!</p>
      <div class="cta-actions">
        <a href="/download/" class="btn btn-primary">
          <i class="fas fa-download"></i> Download Sekarang
        </a>
        <a href="https://t.me/Linux_deepin_ID" target="_blank" rel="noopener" class="btn btn-telegram">
          <i class="fab fa-telegram-plane"></i> Gabung Telegram
        </a>
      </div>
    </div>
  </div>
</section>
