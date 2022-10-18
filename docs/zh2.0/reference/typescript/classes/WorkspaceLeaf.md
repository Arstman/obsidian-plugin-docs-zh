# WorkspaceLeaf

继承自 `WorkspaceItem`

## Constructor

```ts
constructor();
```

## Properties

### view

```ts
view: View
```

## Methods

### openFile

```ts
openFile(file: TFile, openState?: OpenViewState): Promise<void>;
```

默认情况下, `openFile` 会使对应的文件节点高亮。
通过 `{ active: false }` 可以覆盖。

### open

```ts
open(view: View): Promise<View>;
```

### getViewState

```ts
getViewState(): ViewState;
```

### setViewState

```ts
setViewState(viewState: ViewState, eState?: any): Promise<void>;
```

### getEphemeralState

```ts
getEphemeralState(): any;
```

### setEphemeralState

```ts
setEphemeralState(state: any): void;
```

### togglePinned

```ts
togglePinned(): void;
```

### setPinned

```ts
setPinned(pinned: boolean): void;
```

### setGroupMember

```ts
setGroupMember(other: WorkspaceLeaf): void;
```

### setGroup

```ts
setGroup(group: string): void;
```

### detach

```ts
detach(): void;
```

### getIcon

```ts
getIcon(): string;
```

### getDisplayText

```ts
getDisplayText(): string;
```

### onResize

```ts
onResize(): void;
```

### on

```ts
on(name: 'pinned-change', callback: (pinned: boolean) => any, ctx?: any): EventRef;
```

### on

```ts
on(name: 'group-change', callback: (group: string) => any, ctx?: any): EventRef;
```
