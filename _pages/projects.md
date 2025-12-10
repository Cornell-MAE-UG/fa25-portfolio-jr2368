---
layout: default
title: Justice Rose – Projects
permalink: /projects/
---

# Projects

<div class="container my-4">
  <div class="row g-4">

    {% for project in site.projects %}
      <div class="col-12 col-sm-6 col-lg-4">

        <a href="{{ project.url | relative_url }}" class="text-decoration-none text-dark">

          <div class="card h-100 shadow-sm">
            
            {% if project.image %}
            <img src="{{ project.image | relative_url }}" class="card-img-top" alt="{{ project.title }}">
            {% endif %}

            <div class="card-body">
              <h5 class="card-title">{{ project.title }}</h5>
              {% if project.subtitle %}
                <p class="card-text text-muted" style="font-size:0.9rem;">
                  {{ project.subtitle }}
                </p>
              {% endif %}
            </div>

          </div>

        </a>

      </div>
    {% endfor %}

  </div>
</div>
