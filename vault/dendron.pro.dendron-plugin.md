---
id: 87d90002-f480-45eb-a8c4-d00df4d61557
title: Dendron-plugin
desc: ''
updated: 1605465073032
created: 1605375348464
---


# Lookup

```ts
show {
    quickpick := create
    provider := new LookupProvider
    @refreshButtons
    @updatePickerBehavior
    provider.provide quickpick
    quickpick.show
}
```

```ts
refreshButtons(buttons) {
    @state.buttonsPrev = quickpickButtons
    quickpick.buttons = buttons
}
```

```ts
updatePickerBehavior {
    @updateBehaviorByEffect

    if changedNoteType {
        @updateBehaviorByNoteType
    }

    if changedFilterType
        @provider.onUpdatePickerItem

    quickpick.oncreate :=
}
```

## Example
### Normal
- show
- updatePickerBehavior
    - source: updateBehaviorByNoteType(normal)

### Change Value
- updatePickerBehavior
    - source: onValueChange

## Ref

### Times when Picker is Updated
- onUpdatePickerItem
    - lc.show, on init
    - lc.updateBehaviorByNoteType, note type toggle
    - lc.updatePickerBehavior, direct filter toggle

### sources

#### UPDATE_PICKER_FILTER
- when direct filter has changed

#### updatePickerBehavior
- when changing note type
- values
    - normal
    - journal
    - scratch


## Lookup: onButton

- src/components/lookup/LookupControllerV2.ts
```ts
onTriggerButton {

}
```