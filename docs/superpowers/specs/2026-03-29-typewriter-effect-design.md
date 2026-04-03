# Typewriter Effect - Landing Page Text Animation

## Summary
Replace the current fade-in animation on `index.html` with a typewriter (character-by-character typing) effect for all text elements, while the video plays in loop in the background.

## Requirements

### Functional
- All 4 text elements type sequentially: eyebrow → subtitle → title → paragraph
- CTA button appears instantly after paragraph completes
- HTML tags (`<br>`, `<strong>`) are treated as atomic units (not typed character-by-character)
- Video continues looping in background during typing

### Technical
- Pure JavaScript implementation (no external dependencies)
- Typing speed: 35ms per character
- Delay between elements: 300ms
- Initial delay: 1.5s (reduced from 2.5s)
- Responsive: same behavior across all screen sizes

### Code Location
- File: `C:\Users\Admin\SBB-repo\index.html`
- Section: `<script>` block (lines 168-244)
- Replace the current `textPieces.forEach()` animation loop with async `typeText()` function

## Implementation Notes
- Use regex to identify HTML tags and insert them instantly
- Use `async/await` pattern for sequential execution
- Keep existing cursor tracking functionality unchanged
- Keep existing video loading and overlay styles unchanged

## Acceptance Criteria
1. Text appears character-by-character, not fade-in
2. All 4 elements type in sequence with small pauses between
3. HTML inside paragraph renders correctly (bold, line breaks)
4. CTA button appears instantly after paragraph completes
5. Video loops continuously in background