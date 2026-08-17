# Quality, Accessibility, Privacy, and Safety Checklist

## Exercise fidelity

- [ ] Users freely choose the size and shape of their Home Island.
- [ ] They can add anything in their heart using drawings, words, or symbols.
- [ ] Islands around them can hold people, places, objects, groups, or ideas.
- [ ] Every surrounding item can receive a descriptive quality.
- [ ] A shell is one named item; a quality never becomes its own shell.
- [ ] A quality appears as a subtitle on its item's shell, never detached from it.
- [ ] Unnamed drawings are invited to be named when created, not rejected later.
- [ ] Unnamed islands carry a factual ordinal handle, never a content default.
- [ ] No island, item, or quality is ever prefilled with suggested content.
- [ ] Tapping a "Need a starting point?" category is the user's choice, not a default.
- [ ] Gathering lets the user choose what to carry, with a suggestion and no ceiling.
- [ ] Fewer than six carried shells prompts but never blocks.
- [ ] Pairing is random and continues recursively to one final shell.
- [ ] Users, not AI, name every combined meaning.
- [ ] Odd-number rounds are handled without silently dropping an item.
- [ ] Merges are n-ary; a group of three is not a bolted-on special case.
- [ ] A merged shell is the same type as a source shell.
- [ ] Three quality-based sentences come before the reflection questions.
- [ ] All eight original reflection questions are included.
- [ ] Deeper questions remain optional.

## Interaction quality

- [ ] All controls work; no placeholder buttons or TODOs remain.
- [ ] Undo/redo works across drawing, moving, deleting, and labeling.
- [ ] Refresh restores the current stage and data.
- [ ] Refresh does **not** re-deal the pairs — the shuffle seed is persisted.
- [ ] No reshuffle control exists anywhere in the Meaning Maker.
- [ ] Stages 4 and 7 use one map renderer, not two implementations.
- [ ] Long labels and 30+ items do not break the interface.
- [ ] Users can return to earlier stages without losing later work.
- [ ] Exported PDF and PNG match the intended composition.
- [ ] Imported backups are validated and malformed data fails safely.
- [ ] Delete requires confirmation and actually clears local data.

## Accessibility

- [ ] Entire exercise can be completed with a keyboard.
- [ ] A text/list-mode alternative replaces every canvas-only action.
- [ ] Visible focus states and logical focus order are present.
- [ ] Touch targets are at least 44x44px.
- [ ] Text contrast meets WCAG AA.
- [ ] Color is never the sole indicator.
- [ ] Screen readers receive meaningful names, state, and instructions.
- [ ] Dynamic updates such as “paired” or “saved” use restrained live regions.
- [ ] 200% zoom remains usable without lost content.
- [ ] Reduced-motion preferences remove ambient and travel animation.
- [ ] *(Deferred past v1)* RTL and Arabic text render correctly once verified quotations are added.
- [ ] Print/PDF remains legible in grayscale.

## Emotional safety

- [ ] The app says there are no right or wrong answers.
- [ ] "See how it works" explains all seven stages, not a three-bullet summary.
- [ ] The landing page states plainly that nothing here interprets the user.
- [ ] "What am I doing?" is reachable from every stage without losing work.
- [ ] Instructional copy explains process, never content.
- [ ] No worked example, sample island, or illustrative item appears anywhere.
- [ ] It never diagnoses, scores, profiles, or interprets the user.
- [ ] It does not imply that island size, distance, color, or connections have fixed meanings.
- [ ] Every reflection can be skipped or revisited.
- [ ] Users can pause and leave easily.
- [ ] Strong-feelings support copy is present and non-alarmist.
- [ ] The experience is not marketed as therapy or a substitute for care.
- [ ] No streaks, pressure, public galleries, rankings, or forced sharing exist.

## Privacy

- [ ] Work stays on-device by default.
- [ ] No analytics captures reflection text, names, canvas labels, or exports.
- [ ] Any analytics is aggregate, consent-based, and content-blind.
- [ ] Export warns users to review private material before sharing.
- [ ] Users can see what is stored and delete all of it.
- [ ] No hidden cloud sync or AI analysis occurs.
- [ ] JSON backup contains a schema version and no device identifiers.

## Cultural and spiritual respect

- [ ] The core experience is inclusive and works without religious content.
- [ ] Faith context is optional, respectfully framed, and not decorative.
- [ ] The exercise makes no spiritual claim of its own.
- [ ] V1 ships the drawer with English framing only — no Arabic text, no verse citations.
- [ ] *(When added)* Arabic quotations, translations, and citations are independently verified before publication.
- [ ] *(When added)* Sacred text is not cropped, animated frivolously, or used as background texture.

## Final device checks

- [ ] 360px mobile portrait
- [ ] 768px tablet portrait and landscape
- [ ] 1440px desktop
- [ ] Touch-only use
- [ ] Keyboard-only use
- [ ] VoiceOver or NVDA smoke test
- [ ] Slow connection and offline return
- [ ] Light and dark system settings, even if the app uses one intentional theme
- [ ] Chrome, Safari, Firefox, and Edge current versions
