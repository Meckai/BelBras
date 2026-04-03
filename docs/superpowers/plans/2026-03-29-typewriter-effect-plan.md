# Typewriter Effect Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace fade-in text animation with character-by-character typewriter effect on landing page.

**Architecture:** Pure JavaScript implementation using async/await pattern. HTML tags are treated as atomic units (inserted instantly), regular text is typed character-by-character at 35ms intervals. Sequential execution with 300ms pauses between elements.

**Tech Stack:** Vanilla JavaScript, existing HTML/CSS structure unchanged.

---

### Task 1: Create Typewriter Function

**Files:**
- Modify: `index.html` (JavaScript section, lines 168-244)

- [ ] **Step 1: Add delay helper function**

Add after line 168 (inside DOMContentLoaded):

```javascript
const delay = ms => new Promise(resolve => setTimeout(resolve, ms));
```

- [ ] **Step 2: Add typeText function**

Add after the delay function:

```javascript
async function typeText(element, html, speed = 35) {
  // Parse HTML to extract text and tags
  const tempDiv = document.createElement('div');
  tempDiv.innerHTML = html;

  // Get all nodes (text and elements)
  const nodes = Array.from(tempDiv.childNodes);

  element.innerHTML = '';
  element.style.opacity = '1';

  for (const node of nodes) {
    if (node.nodeType === Node.TEXT_NODE) {
      // Type text character by character
      const text = node.textContent;
      for (let i = 0; i < text.length; i++) {
        element.innerHTML += text[i];
        await delay(speed);
      }
    } else if (node.nodeType === Node.ELEMENT_NODE) {
      // Insert element tag instantly (atomic)
      element.appendChild(node.cloneNode(true));
      await delay(10); // Tiny pause after tag
    }
  }
}
```

---

### Task 2: Replace Animation Loop with Sequential Typing

**Files:**
- Modify: `index.html` (JavaScript section)

- [ ] **Step 1: Remove old forEach animation loop**

Delete lines 189-219 (the textPieces.forEach block and its setTimeout wrapper).

- [ ] **Step 2: Add new animateTexts function**

Replace the deleted code with:

```javascript
async function animateTexts() {
  await delay(1500); // Initial delay

  // Create and type eyebrow
  const eyebrow = document.createElement('span');
  eyebrow.className = 'landing-text landing-eyebrow';
  landingContent.appendChild(eyebrow);
  await typeText(eyebrow, textPieces[0].text);

  await delay(300);

  // Create and type subtitle
  const subtitle = document.createElement('p');
  subtitle.className = 'landing-text landing-subtitle';
  landingContent.appendChild(subtitle);
  await typeText(subtitle, textPieces[1].text);

  await delay(300);

  // Create and type title
  const title = document.createElement('h1');
  title.className = 'landing-text landing-title';
  landingContent.appendChild(title);
  await typeText(title, textPieces[2].text);

  await delay(300);

  // Create and type paragraph
  const paragraph = document.createElement('p');
  paragraph.className = 'landing-text landing-subtitle';
  landingContent.appendChild(paragraph);
  await typeText(paragraph, textPieces[3].text);

  // Show CTA button instantly
  const cta = document.createElement('a');
  cta.className = 'landing-text landing-cta';
  cta.href = 'servicos.html';
  cta.innerHTML = textPieces[4].text;
  cta.style.display = 'inline-block';
  cta.style.opacity = '0';
  landingContent.appendChild(cta);
  cta.style.animation = 'fadeInUp 0.8s ease-out forwards';
}

// Start animation
animateTexts();
```

---

### Task 3: Verify and Test

**Files:**
- Test in browser: `index.html`

- [ ] **Step 1: Open index.html in browser**

Open the file directly in browser or use a local server.

- [ ] **Step 2: Verify typewriter effect works**

Check that:
- Video loads and plays in loop
- After 1.5s delay, eyebrow text types character-by-character
- Each element types sequentially with 300ms pauses
- `<br>` and `<strong>` tags in paragraph insert instantly
- CTA button appears with fade-in after paragraph completes
- Cursor tracking still works

- [ ] **Step 3: Commit changes**

```bash
git add index.html
git commit -m "feat: replace fade-in with typewriter effect on landing page

- Add typeText function for character-by-character typing
- Treat HTML tags as atomic units (not typed)
- Sequential animation with 300ms between elements
- Reduce initial delay from 2.5s to 1.5s"
```

---

## Self-Review Checklist

- [x] Spec coverage: All requirements from spec implemented
- [x] No placeholders: All code shown in full
- [x] Type consistency: Function names match across tasks
- [x] File paths: Exact line numbers specified