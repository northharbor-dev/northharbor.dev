---
title: NorthHarbor Development
layout: default
---

<section class="hero">
  <div class="hero__mark">
    <img src="{{ '/assets/beacon-network-avatar-simple.svg' | relative_url }}" alt="NorthHarbor beacon network mark">
  </div>
  <div>
    <span class="hero__eyebrow">Open Source</span>
    <h1>NorthHarbor Development</h1>
    <p>Principled tools and frameworks for human-AI collaboration, developed in public.</p>
  </div>
</section>

<section class="section-card">
  <h2>Projects</h2>
  <p class="section-card__lead">Open source work from NorthHarbor. Each project is independently maintained and openly governed.</p>
  <div class="card-grid">
    {% include project-card.html
      name="HALOS"
      badge="framework"
      url="https://halos.northharbor.dev"
      external=true
      description="Human–Agent Lineage and Origin Standard — a framework for attribution, provenance, and ethical accountability in human–agent collaboration. Built on stable Principles (v1.0) and a technical Provenance Spec (v0.1)." %}
  </div>
</section>

<section class="section-card">
  <h2>Getting Involved</h2>
  <p class="section-card__lead">NorthHarbor projects are developed in public and welcome participation.</p>
  <div class="card-grid">
    <a class="card" href="https://github.com/northharbor-dev" rel="noopener noreferrer">
      <h3>GitHub</h3>
      <p>Source code, issues, and contribution for all NorthHarbor open source projects.</p>
    </a>
    <a class="card" href="https://www.linkedin.com/company/northharbor" rel="noopener noreferrer">
      <h3>Follow Updates</h3>
      <p>Milestones, announcements, and project news on LinkedIn.</p>
    </a>
    <a class="card" href="mailto:hello@northharbor.dev">
      <h3>Contact</h3>
      <p>Questions, feedback, or collaboration ideas are welcome.</p>
    </a>
  </div>
</section>

<section class="section-card">
  <h2>About</h2>
  <p>NorthHarbor Development stewards open source projects focused on responsible human-AI collaboration. Our work is public, our governance is transparent, and our tools are built to be useful today and adaptable tomorrow.</p>
  <p><a href="{{ '/about' | relative_url }}">Read more about NorthHarbor &rarr;</a></p>
</section>
