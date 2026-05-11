# NDGL Design System Mapping

Last reviewed: 2026-05-12

This document maps the current Figma design system, iOS DSKit, and Android core UI design system. Figma edits are made only after explicit approval.

## Source Of Truth Candidates

| Layer | Current source | Notes |
| --- | --- | --- |
| Figma | `Design-System_YAPP-1팀` / `Components` page | Has variables/styles such as `color/bg/interactive/black_900`, `spacing/16`, `border/radius/lg`, and component variants. |
| iOS | `Projects/Modules/DSKit` | UIKit-based DSKit with `Colors.xcassets`, `UIFont.NDGL`, and components such as `NDGLBtn`. |
| Android | `/Users/jihee/workspace/github/NDGL-android/core/ui` | Compose-based design system with `NDGLTheme.colors`, `NDGLTheme.typography`, and `designsystem/*`. |

Recommended shared source: a platform-neutral token file, for example `design-tokens/tokens.json`, generated from the agreed Figma/iOS/Android baseline.

## Naming Policy

| Concept | Recommended shared name | Figma | iOS | Android |
| --- | --- | --- | --- | --- |
| Primary CTA | `primary` | `Type=Primary` | `NDGLBtnStyle.primary` | `NDGLCTAButtonAttr.Type.PRIMARY` |
| Secondary CTA | `secondary` | `Type=Secondary` | `NDGLBtnStyle.secondary` | `NDGLCTAButtonAttr.Type.SECONDARY` |
| Destructive CTA | `destructive` | `Type=Danger` | `NDGLBtnStyle.destructive` | `NDGLCTAButtonAttr.Type.DESTRUCTIVE` |
| Default state | `default` | `State=Default` | normal `UIButton.State` | `Status.ACTIVE` |
| Disabled state | `disabled` | `State=Disabled` | disabled `UIButton.State` | `Status.DISABLED` |
| Filled style | `filled` | `Style=Filled` | primary/secondary/destructive | current CTA implementation |
| Outline style | `outline` | `Style=Outline` | `NDGLBtnStyle.outline` | not present in `NDGLCTAButton`; see `NDGLOutlinedButton` |

Recommendation: standardize product language on `destructive`. Keep `Danger` only as a legacy Figma variant alias if needed.

## Color Tokens

The core palette is aligned between iOS and Android. Figma uses semantic token paths that often point to these primitive values.

| Shared token | Hex | Figma examples | iOS | Android |
| --- | --- | --- | --- | --- |
| `color.white` | `#FFFFFF` | `color/bg/white`, `color/text/interactive/white` | `DSKitAsset.Colors.white.color` | `NDGLTheme.colors.white` |
| `color.black.50` | `#F5F5F5` | `color/bg/interactive/black_50` | `DSKitAsset.Colors.black50.color` | `NDGLTheme.colors.black50` |
| `color.black.100` | `#E6E6E6` | `color/bg/interactive/black_100` | `DSKitAsset.Colors.black100.color` | `NDGLTheme.colors.black100` |
| `color.black.200` | `#D9D9D9` | `color/border/black_200` | `DSKitAsset.Colors.black200.color` | `NDGLTheme.colors.black200` |
| `color.black.300` | `#B3B3B3` | `color/bg/black_300` | `DSKitAsset.Colors.black300.color` | `NDGLTheme.colors.black300` |
| `color.black.400` | `#757575` | `color/text/black_400` | `DSKitAsset.Colors.black400.color` | `NDGLTheme.colors.black400` |
| `color.black.500` | `#444444` | `color/text/black_500` | `DSKitAsset.Colors.black500.color` | `NDGLTheme.colors.black500` |
| `color.black.600` | `#383838` | `color/text/interactive/black_600` | `DSKitAsset.Colors.black600.color` | `NDGLTheme.colors.black600` |
| `color.black.700` | `#2C2C2C` | `color/text/black_700` | `DSKitAsset.Colors.black700.color` | `NDGLTheme.colors.black700` |
| `color.black.800` | `#1E1E1E` | `color/text/interactive/black_800` | `DSKitAsset.Colors.black800.color` | `NDGLTheme.colors.black800` |
| `color.black.900` | `#111111` | `color/bg/interactive/black_900` | `DSKitAsset.Colors.black900.color` | `NDGLTheme.colors.black900` |
| `color.green.50` | `#E9F8ED` | likely `color/bg/green_50` | `DSKitAsset.Colors.green50.color` | `NDGLTheme.colors.green50` |
| `color.green.100` | `#CFF1D8` | likely `color/bg/green_100` | `DSKitAsset.Colors.green100.color` | `NDGLTheme.colors.green100` |
| `color.green.200` | `#A3E4B3` | likely `color/bg/green_200` | `DSKitAsset.Colors.green200.color` | `NDGLTheme.colors.green200` |
| `color.green.300` | `#73D08B` | likely `color/bg/green_300` | `DSKitAsset.Colors.green300.color` | `NDGLTheme.colors.green300` |
| `color.green.400` | `#3EC45B` | likely `color/bg/green_400` | `DSKitAsset.Colors.green400.color` | `NDGLTheme.colors.green400` |
| `color.green.500` | `#15C32D` | likely `color/bg/green_500` | `DSKitAsset.Colors.green500.color` | `NDGLTheme.colors.green500` |
| `color.green.600` | `#10A425` | likely `color/bg/green_600` | `DSKitAsset.Colors.green600.color` | `NDGLTheme.colors.green600` |
| `color.green.700` | `#0C7F1D` | likely `color/bg/green_700` | `DSKitAsset.Colors.green700.color` | `NDGLTheme.colors.green700` |
| `color.green.800` | `#085C15` | likely `color/bg/green_800` | `DSKitAsset.Colors.green800.color` | `NDGLTheme.colors.green800` |
| `color.green.900` | `#04340C` | likely `color/bg/green_900` | `DSKitAsset.Colors.green900.color` | `NDGLTheme.colors.green900` |
| `color.red.50` | `#FEF2F2` | `color/bg/interactive/red_50` | `DSKitAsset.Colors.red50.color` | `NDGLTheme.colors.red50` |
| `color.red.100` | `#FFE2E2` | likely `color/bg/red_100` | `DSKitAsset.Colors.red100.color` | `NDGLTheme.colors.red100` |
| `color.red.200` | `#FFC9C9` | likely `color/bg/red_200` | `DSKitAsset.Colors.red200.color` | `NDGLTheme.colors.red200` |
| `color.red.300` | `#FFA2A2` | likely `color/bg/red_300` | `DSKitAsset.Colors.red300.color` | `NDGLTheme.colors.red300` |
| `color.red.400` | `#FF6467` | likely `color/bg/red_400` | `DSKitAsset.Colors.red400.color` | `NDGLTheme.colors.red400` |
| `color.red.500` | `#FB2C36` | `color/text/red_500` | `DSKitAsset.Colors.red500.color` | `NDGLTheme.colors.red500` |
| `color.red.600` | `#E7000B` | likely `color/bg/red_600` | `DSKitAsset.Colors.red600.color` | `NDGLTheme.colors.red600` |
| `color.red.700` | `#C10007` | likely `color/bg/red_700` | `DSKitAsset.Colors.red700.color` | `NDGLTheme.colors.red700` |
| `color.red.800` | `#9F0712` | likely `color/bg/red_800` | `DSKitAsset.Colors.red800.color` | `NDGLTheme.colors.red800` |
| `color.red.900` | `#82181A` | likely `color/bg/red_900` | `DSKitAsset.Colors.red900.color` | `NDGLTheme.colors.red900` |
| `color.etc.gray` | `#444444` | likely `color/etc/gray` | `DSKitAsset.Colors.etcGray.color` | `NDGLTheme.colors.etcGray` |
| `color.etc.green` | `#15CD3F` | likely `color/etc/green` | `DSKitAsset.Colors.etcGreen.color` | `NDGLTheme.colors.etcGreen` |
| `color.etc.orange` | `#FF6C11` | likely `color/etc/orange` | `DSKitAsset.Colors.etcOrange.color` | `NDGLTheme.colors.etcOrange` |
| `color.etc.purple` | `#5726E7` | likely `color/etc/purple` | `DSKitAsset.Colors.etcPurple.color` | `NDGLTheme.colors.etcPurple` |
| `color.etc.blue` | `#2960EC` | include in shared palette | add to iOS palette if needed | `NDGLTheme.colors.etcBlue` |

## Typography Tokens

The Figma and iOS typography values match closely. Android currently defines font family, weight, and size, but does not encode line height or letter spacing.

Figma authoring rule: when creating or editing text, always apply an existing Figma library Text Style first. Do not directly set `Pretendard`, font size, weight, line height, or letter spacing on text layers unless a matching Text Style does not exist. If no matching style exists, document the missing style and ask whether to add it to the design system.

| Shared token | Figma style | iOS | Android | Size | Weight | Line height | Letter spacing |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `typography.title.lg.bold` | `Title/Lg/Bold` | `.titleLB` | `titleLgBold` | 32 | 700 | 140% | -2.5% |
| `typography.title.lg.semibold` | `Title/Lg/Semi Bold` | `.titleLSB` | `titleLgSemiBold` | 32 | 600 | 140% | -2.5% |
| `typography.title.md.bold` | `Title/Md/Bold` | `.titleMB` | `titleMdBold` | 22 | 700 | 140% | -2% |
| `typography.title.md.semibold` | `Title/Md/Semi Bold` | `.titleMSB` | `titleMdSemiBold` | 22 | 600 | 140% | -2% |
| `typography.subtitle.lg.semibold` | `Subtitle/Lg/Semi Bold` | `.subTitleLSB` | `subtitleLgSemiBold` | 20 | 600 | 140% | -2.5% |
| `typography.subtitle.lg.medium` | `Subtitle/Lg/Medium` | `.subTitleLM` | `subtitleLgMedium` | 20 | 500 | 140% | -2.5% |
| `typography.subtitle.md.bold` | `Subtitle/Md/Bold` | `.subTitleMB` | `subtitleMdBold` | 18 | 700 | 130% | -2.5% |
| `typography.subtitle.md.semibold` | `Subtitle/Md/Semi Bold` | `.subTitleMSB` | `subtitleMdSemiBold` | 18 | 600 | 130% | -2.5% |
| `typography.subtitle.md.medium` | `Subtitle/Md/Medium` | `.subTitleMM` | `subtitleMdMedium` | 18 | 500 | 130% | -2.5% |
| `typography.body.lg.semibold` | `Body/Lg/Semi Bold` | `.bodyLSB` | `bodyLgSemiBold` | 16 | 600 | 130% | -2.5% |
| `typography.body.lg.medium` | `Body/Lg/Medium` | `.bodyLM` | `bodyLgMedium` | 16 | 500 | 130% | -2.5% |
| `typography.body.lg.regular` | `Body/Lg/Regular` | `.bodyLR` | `bodyLgRegular` | 16 | 400 | 130% | -2.5% |
| `typography.body.md.semibold` | `Body/Md/Semi Bold` | `.bodyMSB` | `bodyMdSemiBold` | 14 | 600 | 130% | -2.5% |
| `typography.body.md.medium` | `Body/Md/Medium` | `.bodyMM` | `bodyMdMedium` | 14 | 500 | 130% | -2.5% |
| `typography.body.md.regular` | `Body/Md/Regular` | `.bodyMR` | `bodyMdRegular` | 14 | 400 | 130% | -2.5% |
| `typography.body.sm.semibold` | `Body/Sm/Semi Bold` | `.bodySSB` | `bodySmSemiBold` | 12 | 600 | 120% | -1% |
| `typography.body.sm.medium` | `Body/Sm/Medium` | `.bodySM` | `bodySmMedium` | 12 | 500 | 130% | -2.5% |
| `typography.body.sm.regular` | `Body/Sm/Regular` | `.bodySR` | `bodySmRegular` | 12 | 400 | 130% | -2.5% |

## Spacing And Radius Tokens

| Shared token | Value | Figma | iOS | Android |
| --- | --- | --- | --- | --- |
| `spacing.2` | 2 | `spacing/2` | ad hoc | ad hoc |
| `spacing.4` | 4 | `spacing/4` | ad hoc | ad hoc |
| `spacing.8` | 8 | `spacing/8` | ad hoc | ad hoc |
| `spacing.12` | 12 | `spacing/12` | ad hoc | ad hoc |
| `spacing.16` | 16 | `spacing/16` | ad hoc | ad hoc |
| `spacing.24` | 24 | `spacing/24` | ad hoc | ad hoc |
| `spacing.32` | 32 | `spacing/32` | ad hoc | ad hoc |
| `spacing.40` | 40 | `spacing/40` | ad hoc | ad hoc |
| `spacing.48` | 48 | `spacing/48` | ad hoc | ad hoc |
| `radius.lg` | 8 | `border/radius/lg`, `border/radius/8_lg` | `8.adjustedH` in `NDGLBtn` | `RoundedCornerShape(8.dp)` |
| `radius.rounded` | 999 | `border/radius/rounded` | ad hoc | rounded/pill shapes in components |

Recommendation: add platform-level spacing/radius token accessors after color and typography are stabilized.

## Icon Tokens

| Shared token | Value | Figma | Usage |
| --- | --- | --- | --- |
| `semantic.color.icon.default` | `black.600` / `#383838` | `color/icon/black_600` | Default system icon color |
| `semantic.color.icon.interactive.default` | `black.600` / `#383838` | `color/icon/interactive/black_600` | Interactive icon default |
| `semantic.color.icon.interactive.disabled` | `black.400` / `#757575` | aligns with disabled text/icon decision | Disabled icon color |
| `component.icon.system.size.base` | `24px` | 24px icon components | Base system icon component size |
| `component.button.icon.size.small` | `32px` | small icon button | Compact icon-only button container |

Icon component rule: a 24px Figma icon component should resize its internal vector with `SCALE/SCALE` constraints. This keeps the icon artwork proportional when the component instance is resized.

## Figma Design Authoring Rules

Use these rules when creating or updating Figma screens from this design system.

1. Prefer existing common components and feature components before drawing custom UI.
2. If a similar component already exists, extend it through variants, properties, labels, or instance swaps instead of creating a new local component.
3. Ask for approval before creating a new component when existing components cannot express the required state, content, or interaction.
4. Do not detach shared components or rebuild them locally unless there is an explicit reason and approval.
5. Do not set raw hex colors directly. Use existing semantic color variables for text, background, border, and icon colors.
6. Prefer semantic color tokens such as `color/text/*`, `color/bg/*`, `color/border/*`, and `color/icon/*`. Use primitive palette values only when no semantic intent exists yet.
7. Text must use existing Figma library Text Styles first. Do not manually set `Pretendard`, font size, weight, line height, or letter spacing when a matching `Title/*`, `Subtitle/*`, or `Body/*` style exists.
8. For buttons, navigation bars, chips, modals, bottom sheets, and similar system UI, use component instances and configure their variants/properties.
9. For copy changes inside reusable components, expose and use component properties such as `Label`, `Title`, and `Body` instead of editing detached text layers.
10. When a new variant is needed, add it to the existing component set and connect it to existing icon components, color variables, and text styles.
11. For icon components, keep the component frame at `24x24`, use existing semantic icon color variables, and set internal vector constraints to `SCALE/SCALE`.
12. For product-specific copy, prefer a dedicated editable variant such as `Type=Common` instead of making every fixed semantic type editable.
13. Before handoff, audit the target frames for raw colors, detached component copies, and local text styles. Any exception should be documented.

## Text Style Authoring Policy

| Situation | Required action |
| --- | --- |
| Creating a new text layer | Apply an existing Figma library Text Style before editing copy. |
| Changing typography hierarchy | Switch to another existing Text Style, for example `Body/Md/Semi Bold` to `Subtitle/Md/Semi Bold`. |
| Updating only copy | Keep the current Text Style; edit text content or component `Label` property only. |
| No matching Text Style exists | Do not manually tune font values silently. Document the missing need and decide whether to add a new Text Style. |
| Component text | Expose copy through a component property such as `Label`, `Title`, or `Body`, while keeping the text layer bound to an approved Text Style. |

Manual font assignment is an exception path, not the default. The expected default is: choose a library Text Style, then place or edit the text.

## CTA Button Mapping

| Shared spec | Figma | iOS `NDGLBtn` | Android `NDGLCTAButton` |
| --- | --- | --- | --- |
| Component | `NDGLCTAButton` | `NDGLBtn` | `NDGLCTAButton` |
| Type primary | `Type=Primary` | `.primary` | `Type.PRIMARY` |
| Type secondary | `Type=Secondary` | `.secondary` | `Type.SECONDARY` |
| Type destructive | `Type=Danger` | `.destructive` | `Type.DESTRUCTIVE` |
| State default | `State=Default` | normal state | `Status.ACTIVE` |
| State disabled | `State=Disabled` | disabled state | `Status.DISABLED` |
| Large height | 56 | `56.adjustedH` | `56.dp` |
| Medium height | 40 | `40.adjustedH` | `40.dp` |
| Small height | CTA small is 30; small icon buttons are 32x32 | align to fixed 30 if CTA small is implemented | align CTA small from `32.dp` to `30.dp`; keep icon small at `32.dp` |
| Large text | `Body/Lg/Semi Bold` | `.bodyLSB` | `bodyLgSemiBold` |
| Medium text | `Body/Md/Semi Bold` | `.bodyMSB` | `bodyMdSemiBold` |
| Small text | `Body/Sm/Semi Bold` | `.bodySSB` | `bodySmSemiBold` |
| Large icon | 24 | `24.adjusted` | `24.dp` |
| Medium icon | 20 | `20.adjusted` | `20.dp` |
| Small icon | 16 | `16.adjusted` | `16.dp` |
| Large horizontal padding | 24 | implicit in `UIButton.Configuration` / not explicit | `24.dp` |
| Medium horizontal padding | 16 | implicit in `UIButton.Configuration` / not explicit | align from `24.dp` to `16.dp` |
| Small horizontal padding | 12 | implicit in `UIButton.Configuration` / not explicit | `12.dp` |
| Gap large/medium | 8 | `8` | `8.dp` |
| Gap small | 4 | `4` | `4.dp` |
| Corner radius | 8 | `8.adjustedH` | `8.dp` |
| Primary bg | `black_900` | `#111111` | `black900` |
| Primary fg | `white` | `#FFFFFF` | `white` |
| Secondary bg | `black_50` | `#F5F5F5` | `black50` |
| Secondary fg | `black_700` | `#2C2C2C` | `black700` |
| Destructive bg | `red_50` | `#FEF2F2` | `red50` |
| Destructive fg | `red_500` | `#FB2C36` | `red500` |
| Disabled bg | `black_300` | `#B3B3B3` | align from `black100` to `black300` |
| Disabled fg | `black_400` | `#757575` | align from `black300` to `black400` |

## Navigation And Tab Mapping

| Shared component | Figma | iOS | Android |
| --- | --- | --- | --- |
| Top navigation | `NDGLNavigationBar` | `NDGLNavigationBar` | `NDGLNavigationBar` |
| Search navigation | `NDGLSearchNavigationBar` | `NDGLSearchBar` / search navigation usage | `NDGLSearchNavigationBar` |
| Tab | `NDGLTab` | feature tab components / `TabBarFeature` | `NDGLChipTab`, app bottom nav components |

Follow-up needed: inspect each platform's navigation/tab component APIs and normalize naming before adding or changing screens.

## Icon And Asset Mapping

| Shared convention | Figma | iOS | Android |
| --- | --- | --- | --- |
| Icon size prefix | grouped by 14, 16, 20, 24, 28 | asset names often end in sequence number, e.g. `ic_search2` | drawable names include size, e.g. `ic_28_search.xml` |
| Default icon color | `color/icon/black_600` | use mapped `black600` asset/token | `NDGLTheme.colors.black600` |
| Transport icons | `ic_car`, `ic_walk`, `ic_bus`, etc. | `DSKitAsset.Assets.icCar*`, etc. | `R.drawable.ic_24_car`, `R.drawable.ic_20_bus`, etc. |
| Empty/illustration assets | weather and empty-state assets in Figma | PNG/SVG in `DSKit/Resources/Assets.xcassets` | XML/vector and WebP in `core/ui/src/main/res/drawable*` |

Recent Figma icon updates:

| Figma component | Status | Notes |
| --- | --- | --- |
| `ic_ic_arrow=arrow-up-right` | Added to the icon component set | User adjusted visual style and naming; use the published library component in screen files. |
| `ic_asterisk` | Fixed | Internal `Union` constraints are `SCALE/SCALE`, so the artwork scales with resized component instances. |

Recommendation: establish a single icon naming rule: `ic_{size}_{name}` for Android resources, `ic{Name}{size}` or generated asset aliases for iOS, and Figma component names that include the same size.

## Toast Component Mapping

The current product-file `toast` component set uses fixed semantic variants plus one editable common variant.

| Figma property | Values / behavior | Notes |
| --- | --- | --- |
| `Type` | `AddTravel`, `Delete`, `Transport`, `Edit`, `Common` | Fixed types preserve their original message copy. |
| `Label` | editable text | Connected only to `Type=Common`. |
| `Btn` | boolean | Controls optional action button visibility. |

| Type | Default message |
| --- | --- |
| `AddTravel` | `내 여행에 추가 되었습니다` |
| `Edit` | `장소가 변경되었습니다` |
| `Transport` | `교통수단이 변경되었습니다` |
| `Delete` | `장소가 삭제되었습니다` |
| `Common` | editable via `Label` |

Usage rule: use a fixed `Type` when the toast has one of the known semantic meanings. Use `Type=Common` only for custom copy.

## Current Gaps To Resolve

| Priority | Gap | Why it matters | Suggested resolution |
| --- | --- | --- | --- |
| P1 | Button destructive naming differs: `Danger` vs `destructive` | Causes noisy mapping between Figma and code | Rename/alias Figma variant to `Destructive`, or document `Danger` as legacy alias. |
| P1 | Android typography lacks line height and letter spacing | Text will not match Figma/iOS exactly | Add `lineHeight` and `letterSpacing` to each Android `TextStyle`. |
| P1 | Disabled CTA colors differ on Android | Cross-platform button states will look different | Decision: align Android disabled bg/fg with Figma/iOS: bg `black300`, fg `black400`. |
| P2 | CTA medium horizontal padding differs | Button widths differ across platforms | Decision: use `16` as the shared medium horizontal padding. |
| P2 | CTA small height differs by platform | Small CTA may drift by content/configuration | Decision: CTA small is `30`; icon button small is `32`. |
| P2 | iOS `NDGLBtn` uses hardcoded hex in style enum | Bypasses palette tokens | Replace with `DSKitAsset.Colors.*` after the final token mapping is accepted. |
| P2 | Android has `etcBlue`; iOS/Figma confirmation missing | Palette differs by platform | Decision: include `etcBlue` in the shared color palette. |
| P2 | Toast exists in product design file, not design-system file | Screen file reuse may depend on local product components | Decide whether to move/publish `toast` into the design-system library. |
| P3 | Spacing/radius are not first-class platform tokens | Layout values remain ad hoc | Add typed platform token APIs after colors/typography are stable. |

## Recommended Next Steps

1. Add Android typography line height and letter spacing.
2. Align Android CTA disabled colors, medium padding, and small height with the shared tokens.
3. Add `etcBlue` to iOS/Figma if it is needed in platform assets.
4. Refactor iOS button colors from raw hex to `DSKitAsset.Colors`.
5. Decide whether `toast` should be promoted from the product design file into the design-system library.
6. Use MCP to update Figma variables/components only after explicit approval.
