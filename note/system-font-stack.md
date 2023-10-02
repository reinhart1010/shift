# The complete system font stack

As published on:
+ [Celebrating #InterfaceInPolymorphism through our new system font stack.](https://reinhart1010.id/blog/2022/01/31/celebrating-interfaceinpolymorphism-through-our-new-css-system-font-stack)
+ [The serif system font stack that we’re using right now.](https://reinhart1010.id/blog/2023/10/01/the-serif-system-font-stack-that-were-using-right-now)

## Sans-serif

For regular text:

```css
"Segoe UI Variable Text", -apple-system, BlinkMacSystemFont, Inter, "Segoe UI", Cantarell, "Open Sans", "Noto Sans", Piboto, "HarmonyOS Sans", Ubuntu, "Roboto Flex", Roboto, "Helvetica Neue", FreeSans, Arial, sans-serif`
```

For large text ("Display"):

```css
"Segoe UI Variable Display", -apple-system, BlinkMacSystemFont, Inter, "Segoe UI", Cantarell, "Open Sans", "Noto Sans", Piboto, "HarmonyOS Sans", Ubuntu, "Roboto Flex", Roboto, "Helvetica Neue", FreeSans, Arial, sans-serif`
```

For small text ("Small"):

```css
"Segoe UI Variable Small", -apple-system, BlinkMacSystemFont, Inter, "Segoe UI", Cantarell, "Open Sans", "Noto Sans", Piboto, "HarmonyOS Sans", Ubuntu, "Roboto Flex", Roboto, "Helvetica Neue", FreeSans, Arial, sans-serif`
```

### Additional Recommendations

1. Avoid using italics as Cantarell and other fonts may not offer true italics.
2. Also don't forget to [include the emoji ones](#emoji).
3. If you are unsure whether to use Display or Small variants in websites, we generally recommend using Display for `<h1>`-`<h6>` (or equivalent CSS classes) and Small for `<small>`.

### Design Considerations

1. **Roboto is placed quite at the end of the list** to prevent PC/Mac/Linux devices using it instead of their system fonts.
   + Also consider issues like [this](https://bugs.chromium.org/p/chromium/issues/detail?id=437805) and [this](https://github.com/google/fonts/issues/1568#issuecomment-441352810) where some Windows PC devices renders Roboto text as too thin. Apparently, PC manufacturers are the culprit by silently installing (only) Roboto Thin on their devices.
2. **Roboto Flex is [confirmed](https://android.googlesource.com/platform/external/roboto-flex-fonts/+/be793852ed7c883ad59abd25a6acae72e70e5351) to be placed on Android Open Source Project (AOSP),** starting from Android 14.
3. **We don't want to use Ubuntu as the *de-facto* Linux system font,** just like the case of [Firefox](https://firefoxux.github.io/photon/visuals/typography.html). We respect user's choices for using "pure" [GNOME](https://gnome.org) experience in Ubuntu (`sudo apt install vanilla-gnome-desktop`) by prioritizing [Cantarell](https://cantarell.gnome.org) first before Ubuntu.
4. **We avoided `system-ui` and `ui-sans-serif` due to web browser's different preferences on Linux.** See the point about Ubuntu font.
5. **Some major Linux distributions [decided](https://www.omgubuntu.co.uk/2023/07/ubuntu-noto-fonts-change-mantic) to retire DejaVu fonts (and Bitstream Vera) for Google's Noto fonts.** Noto has also become the default system font for [KDE](https://kde.org) and others.
6. **We internally hate DejaVu Sans for its aged aesthetics and causing too much text reflows compared to others.** For Linux and other Unix devices, we placed [FreeSans](https://www.gnu.org/software/freefont/) as a last resort.

## Serif

For regular text:

```css
ui-serif, "Aptos Serif", Constantia, "Publico Text", Charter, "STIX Two Text", "Libertinus Serif", "Linux Libertine O", "Linux Libertine G", "Linux Libertine", "DejaVu Serif Condensed", "Bitstream Vera Serif Condensed", "Roboto Serif", "Noto Serif", "Times New Roman", serif
```

For large text ("Display")
```
ui-serif, "Aptos Serif", Constantia, "Publico Headline", Charter, "STIX Two Text", "Libertinus Serif", "Linux Libertine O", "Linux Libertine G", "Linux Libertine", "DejaVu Serif Condensed", "Bitstream Vera Serif Condensed", "Roboto Serif", "Noto Serif", "Times New Roman", serif
```
### Additional Recommendations

1. This font stack is **not** optimized for rendering mathematical symbols and equations.
2. Also don't forget to [include the emoji ones](#emoji).

### Design Considerations

1. **We actually avoided Cambria, DejaVu Serif, and Noto Serif for aesthetics reasons.** However, the latter two are still included for compatibility with Android and Linux systems.
2. **We welcome Aptos Serif,** the soon-to-be-the-default serif font for Microsoft Office, as a modern addition to Constantia which is only offered in Regular and Bold.
3. **"Libertinus Serif", "Linux Libertine O", "Linux Libertine G" are practically forks of "Linux Libertine" with different variations.** They are great representatives of the Linux platform, alongside DejaVu. Since major Linux distributions do not include them as fallback fonts to Linux Libertine, we decided to use four of them into the system font stack.

## Monospace

For regular monospaced text without programming ligatures:

```css
ui-monospace, SFMono-Regular, Menlo, "DejaVu Sans Mono", "Bitstream Vera Mono", "Cascadia Mono", Consolas, monospace;
```

For rendering computer code with programming ligatures:

```css
ui-monospace, SFMono-Regular, Menlo, "DejaVu Sans Mono", "Bitstream Vera Mono", "Cascadia Code", Consolas, monospace;
```

### Additional Recommendations

1. **This is still a work in progress.**
2. Note that different programmers prefer different fonts to render computer code (aka. "programming/coding font"). We advise you to allow devs to customize their preferred fonts.
3. Also don't forget to [include the emoji ones](#emoji).

## Emoji

```css
"Apple Color Emoji", "Segoe UI Emoji", SamsungColorEmoji, "Noto Color Emoji Flags", "Noto Color Emoji", "Segoe UI Symbol", "Noto Emoji", Symbola
```

### Design Considerations

1. **Beware of old emoji designs with all its differences.** See <https://reinhart1010.id/browser-test#modern-emoji> for details.
2. **Noto Color Emoji Flags** is still required to render flag emojis in Android devices.
3. **SamsungColorEmoji is currently only supported for Firefox for Android and TizenBrowser (Chromium) on Tizen 6.0 or later.** Chrome and Samsung Internet for Android still renders the Noto Color Emoji one.
4. **Firefox forcibly render emoji ZWJ sequences in default color emoji regardless of custom font-family** - see <https://bugzilla.mozilla.org/show_bug.cgi?id=1845450>
