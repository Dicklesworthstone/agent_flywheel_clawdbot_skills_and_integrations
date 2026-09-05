---
name: ui-ux-polish
description: "Improve an existing interface against agreed usability, accessibility, and visual criteria."
---

# UI/UX Polish — Iterative Enhancement Workflow

> **When to Use:** This is for when your site/app already works and looks decent and you want to improve it. There's a different approach when it looks bad and needs a complete overhaul.
>
> Inspect desktop and mobile behavior separately when both are in scope. Choose changes from observed problems and verify their effect.

---

## The Workflow

### Overview

1. App already works and looks decent
2. Run the polish prompt
3. Agent makes incremental improvements
4. Verify requested improvements on desktop and mobile; repeat only for remaining defects
5. Each pass adds small improvements that compound

### Why Multiple Passes Work

- A new observation can reveal a remaining usability or accessibility defect.
- Repeat a pass only to resolve an identified defect or unmet criterion.
- Parallel work needs authorization and disjoint ownership.
- Stop when the agreed improvements and relevant checks pass.

---

## THE EXACT PROMPT — UI/UX Polish

This prompt is used so frequently it's worth putting on a Stream Deck button:

```
Inspect the requested UI area on desktop and mobile. Identify concrete usability, accessibility, and visual issues; make the highest-impact changes within scope and verify the result. Stop when agreed improvements and relevant checks pass.
```

---

## Evidence and Model Selection

Use actual desktop and mobile observations to choose improvements. Verify
usability, accessibility, and visual changes against the requested outcome.
Select an available model and browser tools that can inspect and verify the
interface. Reasoning settings differ by harness; prompt words do not guarantee
a particular reasoning mode or quality level.

---

## Tech Stack Compatibility

This prompt works with:
- Next.js 16 + React 19 + Tailwind 4
- Any modern web framework
- Applications using Framer Motion or similar animation libraries
- Pretty much anything—it's generic enough to adapt

---

## Iteration Protocol

### Single Agent

```
# First pass
[Run the UI/UX polish prompt]

# Review changes
[Agent makes improvements]

# Further pass, only if a concrete defect remains
[Inspect and correct that defect]

# Stop when the requested improvements and relevant checks pass
```

### Multiple Agents

You can have more than one agent working on UI/UX polish simultaneously:
- They'll focus on different areas
- Use file reservations to avoid conflicts
- Compound improvements faster

---

## When to Use vs. When NOT to Use

### USE This Prompt When:

- App works correctly
- Basic styling is in place
- You want to elevate from "decent" to "world-class"
- Ready for iterative refinement
- Want to optimize for both desktop and mobile

### DON'T Use This Prompt When:

- App is broken or buggy (fix bugs first)
- Styling is fundamentally wrong (need complete overhaul)
- No basic design system in place
- Starting from scratch

For complete overhauls, use a different approach focused on establishing a design system and component library first.

---

## What the Model Typically Improves

### Visual Polish
- Spacing and padding consistency
- Typography hierarchy
- Color contrast and accessibility
- Shadow and depth effects
- Border radius consistency
- Hover/focus states

### Interaction Design
- Button feedback
- Loading states
- Transitions and animations
- Error state handling
- Empty state design

### Mobile Optimization
- Touch target sizes
- Responsive breakpoints
- Mobile-specific navigation
- Gesture support
- Performance on mobile devices

### Desktop Optimization
- Keyboard navigation
- Hover states
- Multi-column layouts
- Sidebar navigation
- Power user shortcuts

---

## Tracking Progress

After each iteration, you might notice:
- Subtle shadow improvements
- Better spacing rhythm
- More consistent typography
- Smoother animations
- Better responsive behavior

Record which observed problems each change resolves. The number of passes is not evidence of quality.

---

## Integration with Beads

When durable tracking is authorized, record scoped UI/UX tasks using the repository's issue workflow:

```bash
br create "Polish homepage UI/UX for desktop" -t enhancement -p 2
br create "Polish homepage UI/UX for mobile" -t enhancement -p 2
br create "Polish dashboard UI/UX for desktop" -t enhancement -p 2
br create "Polish dashboard UI/UX for mobile" -t enhancement -p 2
```

This lets agents work on UI/UX polish as part of the normal bead workflow.

---

## Complete Prompt Reference

### Main Polish Prompt
```
Inspect the requested UI area on desktop and mobile. Identify concrete usability, accessibility, and visual issues; make the highest-impact changes within scope and verify the result. Stop when agreed improvements and relevant checks pass.
```

### Alternative: General Scrutiny (from agent-swarm-workflow)
```
Review the assigned interface and report concrete usability, accessibility, or visual defects against its acceptance criteria. Make changes only when authorized, verify affected desktop and mobile behavior, and stop when the assigned criteria are satisfied.
```

---

## Tips

1. **Finish against criteria**: Stop when the requested improvements and checks pass; repeat only for a concrete remaining defect.
2. **Review changes** — Make sure the model isn't breaking things
3. **Test on real devices** — Desktop browser != mobile experience
4. **Consider accessibility** — WCAG compliance matters
5. **Keep performance in mind** — Pretty but slow is bad UX
