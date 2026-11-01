# Digital Palate: Day 1 Spec (locked)

## Novelty statement
Most food recommenders learn from what you ordered or what's popular. Digital Palate models *why* you like food
as an interpretable vector of flavor, texture, technique, and cuisine, so it can explain every recommendation,
work from the first swipe with no other users' data, and surface dishes from cuisines you've never tried.

## Closed vocabulary
- Flavor (continuous 0-1): sweet, sour, salty, bitter, umami, spicy
- Texture (multi-label): crispy, creamy, chewy, crunchy, tender, flaky, brothy
- Technique (multi-label): grilled, fried, steamed, roasted, baked, simmered, sauteed, raw
- Cuisine (single label): south_indian, north_indian, thai, italian, mexican, chinese, japanese, korean,
  mediterranean, american, middle_eastern
- Ingredients: free list; used for explanations and filters (e.g. vegetarian), NOT in the core score

## Data
- Source: TODO (candidates: Food.com recipes on Kaggle, RecipeNLG). Decide today, max 1 hour.
- Target: 300-500 dishes, balanced across cuisines.

## Tagging
LLM labeling pass into the closed vocabulary, then hand-check ~10% and record the error rate in the README.

## Scoring (v1)
score = 0.45*flavor_cosine + 0.25*texture + 0.20*technique + 0.10*cuisine, then context multiplier,
mapped to 0-100. Cuisine weight is deliberately low to enable cross-cuisine discovery.

## Out of scope for v1
- Collaborative filtering / hybrid models
- Learned embeddings or NLP over reviews
- Real user accounts; context beyond hour and weekday/weekend
- Mobile app

## Day 1 checklist
- [ ] Novelty paragraph said out loud once
- [ ] Vocabulary finalized
- [ ] Dataset chosen
- [ ] Out-of-scope list agreed
- [ ] First commit pushed
