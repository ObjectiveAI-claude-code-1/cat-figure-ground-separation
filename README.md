# cat-figure-ground-separation

Scores how distinctly a cat stands apart in a photograph by evaluating three qualities: form legibility against the background, tonal and textural contrast with the environment, and focal dominance over competing visual elements. High scores mean the cat pops as the undeniable subject; low scores mean it blends in or is visually overshadowed.

## Input

The function accepts a single required field:

| Field | Type | Required | Description |
|---|---|---|---|
| `photograph` | `image` | Yes | A photograph containing a cat. |

The photograph may come from any source — a studio portrait, a phone snapshot, a street photograph, or a wildlife capture. It may contain one cat or multiple cats, be high or low resolution, and be carefully composed or hastily taken. The function assumes a cat is present and evaluates how well that cat separates from everything else in the frame.

## Output

A scalar score in the range **[0, 1]**.

| Score Range | Interpretation |
|---|---|
| **0.8 – 1.0** | The cat achieves near-complete figure-ground separation. Its form is instantly legible, it contrasts powerfully with its environment, and it dominates the frame as the singular focal point. |
| **0.5 – 0.8** | The cat is clearly identifiable as the subject but has moderate weaknesses — some edges may blend, contrast may be unremarkable, or minor competing elements may exist. |
| **0.2 – 0.5** | The cat struggles to separate. Its form partially dissolves into the background, contrast is weak, or other elements in the frame meaningfully compete for the viewer's attention. |
| **0.0 – 0.2** | The cat is nearly lost. It is camouflaged by its surroundings, offers minimal contrast, or is visually overshadowed by dominant competing elements. |

## What It Evaluates

The function evaluates figure-ground separation across two levels and three distinct qualities.

### Level 1 — Separation from Background

How well does the cat visually distinguish itself from its immediate surroundings?

**Quality 1: Form Legibility**

Is the cat's physical shape — its silhouette, outline, and edges — immediately readable at a glance? Form legibility fails when the cat and its background share too much in common: a black cat on a dark blanket, a grey tabby against concrete, a white cat in snow. In these cases the boundary between animal and environment dissolves, and the viewer must work to reconstruct where the cat begins and the background ends. Strong form legibility means the cat's shape is self-evident without study or effort.

**Quality 2: Tonal and Textural Contrast**

How forcefully does the cat assert itself as a distinct visual entity through differences in color, brightness, and texture? Even when a cat's form is technically distinguishable, the degree of contrast determines its visual impact. A ginger cat against a teal wall radiates color contrast. A dark cat in a beam of light achieves brightness contrast. A fluffy Persian on polished marble offers textural contrast. This quality elevates separation from mere visibility to visual impact — the difference between a cat you can find and a cat that finds you.

### Level 2 — Separation from Competing Elements

Does the cat command the viewer's eye without competition from other visual elements?

**Quality 3: Focal Dominance**

Is the cat the singular, commanding focal point of the image, or do other elements compete for the viewer's attention? Competing elements include other animals, human faces, bold or brightly colored objects, and dramatic scenery. A cat can achieve strong focal dominance in a visually rich environment — as long as nothing in that environment rivals its visual weight. What matters is that when the viewer's eye enters the image, it arrives at the cat and stays there.

## Use Cases

### Pet Photography
Photographers reviewing a batch of shots can use this function to surface images where the cat truly commands the frame and discard those where the subject is lost. Useful for professional pet photographers, shelter adoption listings, and casual snapshots alike.

### Content Curation
Social media platforms, editorial teams, photo contests, and any system that selects or ranks cat photographs can use this function as a quality signal. Images with strong figure-ground separation tend to communicate more immediately and satisfy viewer expectations.

### Computational Photography
Image processing tools that adjust backgrounds, apply portrait-mode blur, or enhance subject clarity can use this function as a benchmark — measuring whether their processing improved the cat's visual separation or degraded it.

## Examples

| Scenario | Expected Score | Reasoning |
|---|---|---|
| Orange tabby sitting on a deep blue couch, no other subjects in frame | **High** | Strong color contrast, clear form, no competing elements |
| Black cat lying on a dark grey blanket in a dimly lit room | **Low** | Form dissolves into background, minimal brightness and color contrast |
| White cat on a sunlit windowsill with a busy street scene visible through the glass | **Medium** | Good form legibility and contrast, but the street scene competes for attention |
| Calico cat on a plain wooden floor, centered in frame | **High** | Multi-toned fur contrasts with uniform floor, strong focal dominance |
| Grey cat pressed against a concrete wall with a person and dog also in frame | **Low** | Weak background contrast, strong competition from other subjects |
