# Guide: Using and Expanding the Microbiome Research Content

This guide explains how to use, customize, and expand upon the comprehensive microbiome ecology research content created for this lab website.

## Content Overview

The repository now contains:
- **1 comprehensive literature review** (~11KB)
- **9 detailed pre-proposals** (~7KB each)
- **1 reading list and reference guide** (~8KB)
- **~90KB total** of scientific content

All content is stored in the `_posts/` directory with the date prefix `2026-02-06-`.

## Viewing the Content on Your Website

### Local Development
To view the content locally:
```bash
cd /home/runner/work/lab-website-template/lab-website-template
bundle exec jekyll serve
```
Then navigate to `http://localhost:4000/lab-website-template/blog/` to see all blog posts.

### On GitHub Pages
Once the repository is pushed, the content will be automatically available at:
- Main blog page: `https://[username].github.io/lab-website-template/blog/`
- Individual posts: `https://[username].github.io/lab-website-template/blog/YYYY-MM-DD-post-name/`

## Customizing the Content

### 1. Update Author Information
Each post has front matter that can be customized:
```yaml
---
title: "Your Title"
tags:
  - tag1
  - tag2
author: Your Name or Lab Team
---
```

To change the author for all posts:
```bash
# Find and replace in all posts
cd _posts
sed -i 's/author: Lab Team/author: Your Name/g' 2026-02-06-*.md
```

### 2. Add Your Own Tags
Tags help organize content. Add tags relevant to your research:
```yaml
tags:
  - your-research-area
  - specific-organism
  - technique
  - funding-agency
```

### 3. Update Research Focus
To emphasize your specific research:
1. Edit the main literature review to highlight your lab's work
2. Add sections about your ongoing projects
3. Link pre-proposals to your actual research initiatives

## Adding Citations

### Finding DOIs
To add proper citations for papers by the target researchers:

1. **PubMed Search:**
   ```
   Sanchez A[Author] AND Yale[Affiliation] AND metabolic
   ```

2. **Google Scholar:**
   - Search: `author:"A Sanchez" "Yale University"`
   - Click "Cite" → Copy DOI

3. **Lab Websites:**
   - Gore Lab: https://www.gore.mit.edu/publications
   - Find publication pages for other labs

### Adding DOIs to sources.yaml
1. Open `_data/sources.yaml`
2. Add entries in this format:
   ```yaml
   - id: doi:10.1234/journal.12345
     tags:
       - relevant-tag
       - another-tag
   ```

3. Run citation generator:
   ```bash
   bash cite.sh
   ```

### Citing in Your Documents
Once citations are generated, reference them in markdown:
```markdown
According to recent work {% cite doi:10.1234/journal.12345 %}, bacterial-fungal interactions...
```

Or create a references section:
```markdown
## References
{% bibliography --cited %}
```

## Expanding the Pre-Proposals

### Converting to Full Proposals
Each pre-proposal can be expanded into a full grant proposal:

1. **Add More Detail to Each Section:**
   - Expand background to 2-3 pages
   - Add preliminary data section (3-4 pages)
   - Detail specific aims with hypotheses (2 pages each)
   - Expand methods with protocols (5-10 pages)
   - Add more detailed timeline (Gantt chart)
   - Include budget and justification

2. **Add Required Sections:**
   - Significance and innovation (separate sections)
   - Approach (detailed methods per aim)
   - Personnel qualifications
   - Resources and environment
   - Data management plan
   - Collaboration letters

3. **Include Figures:**
   - Conceptual diagrams
   - Preliminary data figures
   - Workflow diagrams
   - Expected results

### Creating New Pre-Proposals
Use existing pre-proposals as templates:

```bash
cp _posts/2026-02-06-preproposal-1-bacterial-fungal-communication.md \
   _posts/2026-02-06-preproposal-10-your-topic.md
```

Then modify:
1. Change title and tags in front matter
2. Update background to your topic
3. Revise knowledge gaps
4. Adjust specific aims
5. Customize methods for your approach

## Fact-Checking and Verification

### Before Publication or Grant Submission
1. **Verify Researcher Information:**
   - Check current affiliations (researchers move)
   - Verify recent publications
   - Confirm research focus areas

2. **Validate Scientific Claims:**
   - Cross-reference with primary literature
   - Check citation counts for "highly cited" claims
   - Verify technical details

3. **Update Statistics:**
   - Replace placeholder numbers with actual data
   - Cite sources for epidemiological statistics
   - Update disease burden estimates

### Recommended Verification Process
```bash
# Create a verification checklist
cat > verification_checklist.md << EOF
## Verification Checklist for [Document Name]

- [ ] All researcher affiliations verified (check lab websites)
- [ ] All cited papers exist and are correctly attributed
- [ ] Statistics have primary source citations
- [ ] Technical methods are feasible with available technology
- [ ] Timeline is realistic
- [ ] Budget (if added) is appropriate
- [ ] All claims are supported by literature
EOF
```

## Integrating with Lab Research

### Linking to Actual Projects
1. **Update Pre-Proposals with Real Data:**
   - Replace "preliminary data" placeholders with actual results
   - Add figures from your experiments
   - Include pilot study outcomes

2. **Create Progress Updates:**
   ```bash
   # Create a new post updating progress
   cat > _posts/$(date +%Y-%m-%d)-project-update-bacterial-fungal.md
   ```

3. **Link Related Content:**
   ```markdown
   See our [original pre-proposal](/blog/2026-02-06-preproposal-1-bacterial-fungal-communication/)
   for the initial concept.
   ```

### Showcasing Publications
When papers are published based on this work:
1. Add to `_data/sources.yaml`:
   ```yaml
   - id: doi:10.1234/your.paper
     tags:
       - lab-publication
       - bacterial-fungal
   ```

2. Create announcement post:
   ```markdown
   ---
   title: "New Publication: Bacterial-Fungal Communication"
   tags:
     - publication
     - bacterial-fungal interactions
   ---
   
   We're excited to announce our new paper...
   [Link to pre-proposal that inspired this work]
   ```

## Collaborating with Target Researchers

### If Pursuing Actual Collaboration
1. **Email Template:**
   ```
   Dear Dr. [Name],
   
   I'm writing to explore potential collaboration in [area]. 
   Our lab has developed pre-proposals in [specific topic], inspired 
   by your work on [their research area].
   
   [Link to your website/pre-proposal]
   
   Would you be interested in discussing potential synergies?
   ```

2. **Update Content:**
   - If collaboration develops, update pre-proposals to reflect partnership
   - Add collaborator names to author fields
   - Note collaboration in methods sections

## Maintaining Content Currency

### Regular Updates
Set reminders to:
- **Quarterly:** Check for new papers from target researchers
- **Semi-annually:** Update statistics and disease burden numbers
- **Annually:** Review all pre-proposals for continued relevance

### Tracking Changes
Use git to track content evolution:
```bash
# See history of a specific document
git log --follow _posts/2026-02-06-preproposal-1-bacterial-fungal-communication.md

# Compare versions
git diff HEAD~5 _posts/2026-02-06-microbiome-ecology-literature-review.md
```

## Tips for Grant Writing

### Converting to Specific Agency Formats

**NIH R01:**
- Expand to ~12 pages research plan
- Add 1 page for specific aims
- Include progress report if renewal
- Follow PHS 398 format

**NSF:**
- Limit to 15 pages project description
- Separate 1-page documents for broader impacts
- Include data management plan
- Follow NSF PAPPG guidelines

**Foundation Grants:**
- Often 2-5 page limit (pre-proposals are sized for this!)
- Focus on innovation and impact
- Less methodological detail
- Emphasize translational potential

### Reusing Content
The modular structure allows mixing and matching:
- Use literature review as grant background
- Extract specific aims from pre-proposals
- Combine multiple pre-proposals for larger projects
- Use knowledge gaps as significance section

## Troubleshooting

### Jekyll Build Errors
If posts don't display:
```bash
# Check YAML front matter is valid
head -15 _posts/2026-02-06-problematic-post.md

# Test build
bundle exec jekyll build --trace
```

### Citation Issues
If auto-cite fails:
```bash
# Test individual DOI
python auto-cite/auto-cite.py test doi:10.1234/test

# Check sources.yaml syntax
python -m yaml _data/sources.yaml
```

### Large Files
If posts become too large (>1MB):
- Split into multiple posts
- Move detailed methods to supplementary documents
- Link between related posts

## Getting Help

### Resources
- **Jekyll Documentation:** https://jekyllrb.com/docs/
- **Manubot:** https://manubot.org/
- **Markdown Guide:** https://www.markdownguide.org/

### Community
- Jekyll talk forum
- GitHub issues for this template
- Lab website template documentation

## Next Steps

1. **Immediate:**
   - Review all content for accuracy
   - Add specific DOIs from target researchers
   - Customize author fields

2. **Short-term (1-2 weeks):**
   - Add preliminary data if available
   - Create figures/diagrams
   - Set up collaboration emails

3. **Medium-term (1-3 months):**
   - Expand priority pre-proposals to full proposals
   - Submit to appropriate funding agencies
   - Track and document progress

4. **Long-term (6-12 months):**
   - Update with published results
   - Add new pre-proposals for emerging areas
   - Build collaborative network

---

This content represents a significant foundation for research planning, grant writing, and scientific communication. Use it strategically to advance your research program!
