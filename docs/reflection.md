# Design reflection

## State and persistence

The most useful constraint was HTML/CSS-only state. Native radios and checkboxes can represent choices, but they cannot store progress across documents. The design therefore tells the player that each page has local state and provides a journal order and field notebook. A production game with persistent inventory would need a different technical scope.

## Readability and atmosphere

Deep green and brass establish a workshop mood. Parchment-colored body text and restrained spacing preserve readability. Native system fonts keep the site available offline. The trade-off is less precise control over typography across operating systems.

## Motion with purpose

The clock gears establish the setting. Short card and button transitions acknowledge interaction. The vault sequence gives a clear ending. Continuous decoration can be paused, and reduced motion preserves all state changes without movement.

## Maintainability

Ten commented HTML/CSS files divide presentation and interaction rules while one stylesheet entry keeps page integration consistent. The repeated header/footer markup is deliberate under the no-server-language rule. A future implementation could use build-time templates if the course scope allowed them.

## Further improvements to assess after testing

Use actual classmate feedback to decide whether hint wording or digit controls need refinement. Record specific observations, changes, and retests here. Add individual lessons in each member’s own words after reviewing and explaining the code.
