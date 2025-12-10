---
layout: default
title: Projects
permalink: /projects/
---

<style>
/* Page Title */
.projects-title {
  font-size: 2.4rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  border-bottom: 3px solid #ddd;
  padding-bottom: 0.5rem;
}

/* Project Grid Layout */
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}

/* Project Card */
.project-card {
  background: #ffffff;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 4px 10px rgba(0,0,0,0.08);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  text-decoration: none;
  color: inherit;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 18px rgba(0,0,0,0.15);
}

/* Uniform Image Styling */
.project-card img {
  width: 100%;
  height: 220px;         /* Force uniform image height */
  object-fit: cover;     /* Ensures images scale/crop nicely */
  background: #f2f2f2;
}

/* Title Styling */
.project-card-title {
  font-size: 1.2rem;
  font-weight: 600;
  padding: 1rem;
  flex-grow: 1;
}
</style>


<h1 class="projects-title">Projects</h1>

<div class="project-grid">

  {% for project in site.projects %}
    <a href="{{ project.url | relative_url }}" class="project-card">
      
      {% if project.image %}
      <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
      {% else %}
      <img src="https://via.placeholder.com/600x400?text=No+Image" alt="Placeholder">
      {% endif %}
      
      <div class="project-card-title">
        {{ project.title }}
      </div>

    </a>
  {% endfor %}

</div>
