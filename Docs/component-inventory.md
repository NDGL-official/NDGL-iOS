# NDGL Component Inventory

Last reviewed: 2026-05-12

This document organizes reusable components and patterns found in the current Figma product design file. The goal is to reuse existing components as much as possible when designing new screens, and to keep any new components visually consistent with the existing NDGL design language.

Initial Figma inspection was read-only. Later Figma cleanup was applied only after approval.

## Sources

| Source | URL / Node | Purpose |
| --- | --- | --- |
| Design system | `z4YahfTF6uMPZ37JpUPT0p`, node `53:1801` | Foundation tokens and common design-system components |
| Product screens | `qHn9o58ENLeHjiBWNuZFJx`, node `538:4616` | Completed screen examples |
| Feature components | `qHn9o58ENLeHjiBWNuZFJx`, node `2288:10267` | Reusable components used inside feature screens |
| Toast component | `qHn9o58ENLeHjiBWNuZFJx`, node `564:9130` | Product-file toast component set |

## Reuse Decision Flow

Use this order when creating a new screen:

1. Use foundation tokens first: color, typography, spacing, radius, icon size.
2. Reuse common components when available: navigation, CTA, icon button, tab, checkbox, modal, bottom sheet.
3. Reuse feature components when the screen belongs to the same domain or interaction pattern.
4. Reuse an existing pattern when no single component fits but a similar screen structure exists.
5. Create a new local component only when the existing component cannot support the required state, content, or interaction.
6. Promote a new component to feature/common inventory only if it is likely to be reused.

## Component Categories

| Category | Meaning | Design action | Code action |
| --- | --- | --- | --- |
| Foundation | Tokens and primitive styles | Must use existing variables/text styles | Map to shared design tokens |
| Common component | Reusable across many features | Prefer direct reuse or variant extension | Implement in DSKit/core UI |
| Feature component | Reusable within a product area | Reuse within similar feature screens | Implement in feature module or shared feature UI |
| Pattern | Repeated screen composition | Copy structure, then adapt content | Consider screen template/composable helper |
| One-off | Screen-specific layout or asset | Keep local unless repeated | Keep inside owning screen |
| Needs cleanup | Existing item with naming/state ambiguity | Rename, classify, or merge after approval | Avoid new API until naming is resolved |

## Foundation Reference

| Area | Current baseline | Notes for new screens |
| --- | --- | --- |
| Typography | Figma library Text Styles | Always apply existing Figma Text Styles first. Do not manually assign Pretendard, size, weight, line height, or letter spacing unless a matching style does not exist. |
| Colors | Shared primitive and semantic variables | Use semantic tokens first; primitive colors only when semantic intent is unclear. |
| Spacing | `2`, `4`, `8`, `12`, `16`, `24`, `32`, `40`, `48` | Prefer existing spacing scale. Screen horizontal padding appears to use `16` frequently. |
| Radius | `8`, rounded/pill | Cards and buttons generally use restrained radius; avoid introducing a new radius casually. |
| CTA small | height `30` | Different from icon small. Use only for text CTA buttons. |
| Icon small | size `32` | Different from CTA small. Use for compact icon-only actions. |
| System icon | size `24`, color `color/icon/black_600` | Internal artwork should use `SCALE/SCALE` constraints so resized instances scale correctly. |

## Common Components

| Component | Figma name(s) | Reuse priority | Expected use | Notes |
| --- | --- | --- | --- | --- |
| Top navigation | `Top Navigation`, `NDGLNavigationBar` | High | Screen-level navigation, title, back/search/actions | Reuse before creating a custom header. Confirm variants for title/search/action combinations. |
| Bottom navigation | `BottomNavigationBar`, variants `Info`, `Home`, `Mytrip` | High | App-level main navigation | Treat as app shell component. Do not redesign per screen. |
| CTA button | `NDGLCTAButton`, `BUTTON` | High | Primary, secondary, destructive, outline actions | CTA small is `30`; medium horizontal padding is `16`; outline maps to `button.cta.outline`. |
| Icon button | `BtnIcon`, `GroupBtn` | High | Icon-only actions, floating actions, compact controls | Small icon button is `32`; larger floating action appears as `56`. Keep separate from CTA sizing. |
| Button stack | `BtnStack` | Medium | Paired or grouped actions | Reuse for bottom actions or modal actions if layout matches. |
| Tab | `Tab`, `PrimitiveTap`, `Tap`, `TapGroup` | High | Category/date/content switching | There are several tab-like components. Consolidate naming before adding new variants. |
| Checkbox | `Check` | Medium | Selection states | Reuse for binary selection. Confirm selected/disabled variants if needed. |
| Chip | `Chips`, `Tag`, `TagCountry`, `tag_category` | High | Filters, labels, selected tags | Multiple tag/chip families exist. Choose based on behavior: selectable chip vs static label vs category tag. |
| Modal | `Modal` | Medium | Blocking confirmation or success states | Multiple modal definitions exist. Pick one base and extend variants after cleanup. |
| Bottom sheet | `Bottom Sheet`, `BottomSheet` | Medium | Transport picker, time picker, search/store summary | Naming and type structure should be normalized before creating new bottom sheet variants. |
| Toast | `toast` | High | Temporary feedback after add/edit/delete/transport actions | Fixed semantic types keep original copy. Use `Type=Common` plus `Label` for custom copy. |

## Feature Components

| Component | Figma name(s) | Domain | Reuse priority | Expected use | Notes |
| --- | --- | --- | --- | --- | --- |
| Trip summary card | `CardTripSummary`, variants `None`, `Ongoing`, `Upcoming`, `Completed`, `Selected` | My trip / itinerary | High | Trip list, trip status summary, selectable trip item | Strong candidate for reusable feature component. |
| Trip card | `CardTrip` | My trip / itinerary | Medium | Trip preview or card content | Renamed from `CardTirp`. Confirm relationship with `CardTripSummary`. |
| Info video card | `InfoVideo`, states `card_accordion_on`, `card_accordion_off` | Content/detail | High | Expandable video/info module | Good state model. Use for accordion-like content before making a new pattern. |
| Thumbnail card | `CardThumbnail`, variants `Card01`, `Card02` | Search/content | Medium | Thumbnail-based content entry | Confirm image ratio and text rules before reuse. |
| Search card list | `SearchCardList` | Search | High | Search results or selectable list entries | Reuse for search-like flows. |
| Search list | `SearchList`, variants `Search`, `History` | Search | High | Search result and recent-search views | Keep search/history variants together. |
| Place info row | `info_place` | Place/detail | High | Airport, automobile, attraction, restaurant, cafe, stay metadata | Renamed from `info_palce`; variant `resturant` was renamed to `restaurant`. |
| Transit time info | `info_transit_time` | Place/detail / route | High | Car, train, walk, bus, bicycle, ferry, taxi, two-wheeler, airplane duration | Good feature primitive for route/detail screens. |
| Category card | `card_category`, `Card` | Place/category | Medium | Category selection or categorized place cards | Confirm whether `card_category` and `Card` are duplicate concepts. |
| Detail card | `card_detail` | Place/detail | Medium | Detailed content grouping | Needs closer visual/state audit before reuse. |
| Title card | `card_title` | Place/detail | Medium | Section title or highlighted content | Reuse if typography/layout matches target screen. |
| Content block | `contents` | Content/detail | Medium | Detail content display | Needs clearer component responsibility. |
| Budget | `budget`, variants `default`, `card` | Trip planning | Medium | Budget display or budget entry summary | Useful if new screen includes cost/planning. |
| Plan B | `PlanB` | Trip planning | Medium | Alternative plan suggestion | Keep as feature-specific until repeated elsewhere. |
| Weather card | `CardWeather`, variants `Sunny`, `SunnyRain`, `SunCloud`, `Cloud`, `RainCloud` | Trip/detail | High | Weather forecast/status card | Reuse for itinerary/weather contexts. |
| Empty state illustration | `EmptySpace`, `EmptySpaceResource` | Empty state | Medium | Empty list or resource unavailable states | Renamed from `EmptySapceResource`. Confirm size variants `Md`, `Lg`. |
| Weather icon asset | `IconWeather` | Asset | High | Weather state iconography | Reuse exact assets for weather consistency. |
| Image asset | `Asset`, variants `Img01`, `Img02` | Asset | Low | Placeholder or illustration asset | Treat as asset, not UI component, unless usage repeats. |

## Reusable Patterns

| Pattern | Existing components | Reuse when | Notes |
| --- | --- | --- | --- |
| Search experience | `Top Navigation`, `Chips`, `SearchList`, `SearchCardList`, `BottomSheet` | New screen has search, filters, history, or result picking | Start from existing search screen structure before designing a new search flow. |
| Trip list/status | `CardTripSummary`, `CardTrip`, `BottomNavigationBar` | New screen shows current/upcoming/completed trips | Use existing trip state language. Avoid introducing new status colors without token review. |
| Place/detail info | `info_place`, `info_transit_time`, `card_detail`, `contents`, `CardWeather` | New screen shows place metadata, travel time, weather, or detail content | Good candidate pattern for itinerary detail and place detail screens. |
| Filter/category selection | `Chips`, `Tag`, `TagCountry`, `PrimitiveTap`, `Tap` | User selects category, country, date, or content type | Decide whether interaction is chip, tag, or tab before composing. |
| Bottom action area | `NDGLCTAButton`, `BtnStack`, `BottomSheet` | Screen ends in one or two key actions | Reuse sticky CTA behavior from existing screens; clarify scroll vs fixed behavior in handoff. |
| Confirmation flow | `Modal`, `BottomSheet`, `BtnStack` | User confirms, changes, or completes an operation | Normalize modal/bottom sheet naming before adding another confirmation pattern. |
| Empty state | `EmptySpace`, `EmptySpaceResource`, CTA button | Screen has no data or no saved resource | Keep illustration size and copy tone consistent with existing empty screens. |
| Toast feedback | `toast` | User completes add/edit/delete/transport action or needs short custom feedback | Use fixed `Type` for known cases. Use `Common` only when the message does not match an existing type. |

## Cleanup Status

| Status | Item | Previous issue | Resolution |
| --- | --- | --- | --- |
| Done | `CardTrip` | Was `CardTirp` | Renamed after approval. |
| Done | `info_place` | Was `info_palce` | Renamed after approval. |
| Done | `restaurant` category | Was `resturant` | Renamed after approval. |
| Done | `EmptySpaceResource` | Was `EmptySapceResource` | Renamed after approval. |
| Done | `TimePicker` | Was `TimePikcer` | Renamed after approval. |
| Done | `ic_asterisk` constraints | Internal `Union` did not scale with resized instances | Set internal vector constraints to `SCALE/SCALE`. |
| Done | `toast` copy behavior | All variants were temporarily bound to one editable `Label` | Restored fixed copy for `AddTravel`, `Edit`, `Transport`, `Delete`; kept editable `Label` only on `Common`. |
| Done | `ic_ic_arrow=arrow-up-right` | New icon needed reusable component status | Added as 24px icon component; user adjusted final style/naming. |

## Needs Cleanup Before Heavy Reuse

| Priority | Item | Current issue | Suggested resolution |
| --- | --- | --- | --- |
| P2 | `Bottom Sheet` vs `BottomSheet` | Same concept appears with different naming | Choose one naming convention. Recommended: `BottomSheet`. |
| P2 | Multiple `Modal` definitions | Duplicate names make reuse and code mapping ambiguous | Merge into one modal component set or prefix by domain. |
| P2 | `Tab`, `Tap`, `PrimitiveTap`, `TapGroup` | Similar controls with mixed naming | Decide whether product term is `Tab`; keep `Tap` only if intentionally used in Korean/Figma context. |
| P2 | `Tag`, `TagCountry`, `tag_category`, `Chips` | Static labels and selectable chips are mixed | Split by behavior: `ChipSelectable`, `TagStatic`, `TagCountry`, `TagCategory`. |
| P2 | `btn_small` height `20` | Could be confused with CTA small `30` | Treat as a separate inline/action button token or feature component. |
| P2 | `toast` is in product file | It is reusable, but not yet a design-system library component | Decide whether to promote/publish it into `Design-System_YAPP-1팀`. |

## New Screen Workflow

Use this checklist before drawing a new screen:

| Step | Question | Output |
| --- | --- | --- |
| 1. Screen intent | What job does this screen do? | One-line screen purpose |
| 2. States | Does it need loading, empty, error, permission, success, disabled states? | Required state list |
| 3. Existing pattern | Is there a similar screen or flow? | Reference frame/component link |
| 4. Common components | Which navigation, CTA, tabs, chips, modals, bottom sheets can be reused? | Component list |
| 5. Feature components | Which cards, list rows, info blocks, weather/search/trip components can be reused? | Component list |
| 6. New components | What remains impossible to express with existing components? | New component candidate list |
| 7. Token check | Are all colors, Text Styles, spacing, radius, and icon sizes from the token set/library? | Token exceptions list |
| 8. Handoff notes | Are sticky areas, scroll behavior, truncation, and empty/error states clear? | Dev notes |

## New Component Criteria

Create a new component only when at least one of these is true:

| Condition | Example |
| --- | --- |
| Existing component cannot support the required content structure | A card needs a timeline, price, and route summary while existing cards support only title/image/body |
| Existing component has the wrong interaction model | Static tag is not suitable for a selectable filter |
| Existing component would require visually awkward overrides | Too many detached spacing/color/text changes would be needed |
| The pattern is likely to repeat | A new itinerary step row appears in multiple trip-planning screens |

Keep a new component local to the screen when it is used once and is tightly tied to that specific screen.

## Visual Consistency Rules

| Area | Rule |
| --- | --- |
| Typography | Use existing Figma library Text Styles first. Match hierarchy from similar screens by switching styles, not by manually editing font values. |
| Color | Use semantic variables first. Avoid new ad hoc colors. |
| Cards | Follow existing card padding, radius, and image/text hierarchy before inventing a new card style. |
| Lists | Reuse existing search/place/trip row patterns. Clarify divider and row height behavior. |
| CTA | Use `NDGLCTAButton` for main actions. Do not use inline small buttons as CTA replacements. |
| Icon actions | Use `BtnIcon`; keep small icon button at `32`. |
| Icons | Use 24px icon components for system icons; internal vectors should scale with the component frame. |
| Chips/tags | Use selectable chips only for user choice; static tags only for metadata labels. |
| Modal/bottom sheet | Prefer existing modal/bottom sheet structure and button placement. |
| Toast | Use fixed `Type` variants for known messages; use `Type=Common` and `Label` for custom messages. |
| Empty state | Reuse existing illustration scale and short copy tone. |

## Recommended Next Steps

1. Decide whether `toast` should be promoted from the product design file into the design-system library.
2. Run a variable/style binding audit on the feature component section.
3. Group feature components by product domain in Figma: navigation/actions, search, trip, place/detail, bottom sheet/modal, empty/assets.
4. Pick the first new screen and draft it using only existing components first.
5. List any missing parts as new component candidates before creating them.
