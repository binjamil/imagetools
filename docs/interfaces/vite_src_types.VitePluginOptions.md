[imagetools](../README.md) / [Modules](../modules.md) / [vite/src/types](../modules/vite_src_types.md) / VitePluginOptions

# Interface: VitePluginOptions

[vite/src/types](../modules/vite_src_types.md).VitePluginOptions

## Table of contents

### Properties

- [defaultDirectives](vite_src_types.VitePluginOptions.md#defaultdirectives)
- [exclude](vite_src_types.VitePluginOptions.md#exclude)
- [force](vite_src_types.VitePluginOptions.md#force)
- [include](vite_src_types.VitePluginOptions.md#include)
- [removeMetadata](vite_src_types.VitePluginOptions.md#removemetadata)
- [resolveConfigs](vite_src_types.VitePluginOptions.md#resolveconfigs)
- [silent](vite_src_types.VitePluginOptions.md#silent)

### Methods

- [extendOutputFormats](vite_src_types.VitePluginOptions.md#extendoutputformats)
- [extendTransforms](vite_src_types.VitePluginOptions.md#extendtransforms)

## Properties

### defaultDirectives

• `Optional` **defaultDirectives**: `URLSearchParams` \| (`url`: `URL`) => `URLSearchParams`

This option allows you to specify directives that should be applied _by default_ to every image.
You can also provide a function, in which case the function gets passed the asset ID and should return an object of directives.
This can be used to define all sorts of shorthands or presets.

**`example`**
```js
import { defineConfig } from 'vite'
import { imagetools } from 'vite-imagetools'

export default defineConfig({
 plugins: [
   imagetools({
      defaultDirectives: (url) => {
       if (url.searchParams.has('spotify')) {
          return new URLSearchParams({
            tint: 'ffaa22'
          })
        }
        return new URLSearchParams()
      }
    })
   ]
})
```

#### Defined in

[vite/src/types.ts:42](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L42)

___

### exclude

• **exclude**: `string` \| `RegExp` \| (`string` \| `RegExp`)[]

What paths to exclude when processing images.
This defaults to the public dir to mirror vites behavior.

**`default`** 'public\/**\/*'

#### Defined in

[vite/src/types.ts:14](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L14)

___

### force

• `Optional` **force**: `boolean`

This option used to enable the plugin during development mode. This option is no longer required!

**`deprecated`**

#### Defined in

[vite/src/types.ts:80](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L80)

___

### include

• **include**: `string` \| `RegExp` \| (`string` \| `RegExp`)[]

Which paths to include when processing images.

**`default`** '**\/*.{heic,heif,avif,jpeg,jpg,png,tiff,webp,gif}?*'

#### Defined in

[vite/src/types.ts:8](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L8)

___

### removeMetadata

• **removeMetadata**: `boolean`

Wether to remove potentially private metadata from the image, such as exif tags etc.

**`default`** true

#### Defined in

[vite/src/types.ts:74](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L74)

___

### resolveConfigs

• `Optional` **resolveConfigs**: (`entries`: [`string`, `string`[]][], `outputFormats`: `Record`<`string`, `OutputFormat`\>) => `Record`<`string`, `string` \| `string`[]\>[]

#### Type declaration

▸ (`entries`, `outputFormats`): `Record`<`string`, `string` \| `string`[]\>[]

This function builds up all possible combinations the given entries can be combined
an returns it as an array of objects that can be given to a the transforms.

##### Parameters

| Name | Type | Description |
| :------ | :------ | :------ |
| `entries` | [`string`, `string`[]][] | The url parameter entries |
| `outputFormats` | `Record`<`string`, `OutputFormat`\> | - |

##### Returns

`Record`<`string`, `string` \| `string`[]\>[]

An array of directive options

#### Defined in

[vite/src/types.ts:62](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L62)

___

### silent

• **silent**: `boolean`

Settings this option to true disables all warnings produced by this plugin

**`default`** false

#### Defined in

[vite/src/types.ts:68](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L68)

## Methods

### extendOutputFormats

▸ `Optional` **extendOutputFormats**(`builtins`): `Record`<`string`, `OutputFormat`\>

You can use this option to extend the builtin list of output formats.
This list will be merged with the builtin output formats before determining the format to use.

**`default`** []

#### Parameters

| Name | Type |
| :------ | :------ |
| `builtins` | `Record`<`string`, `OutputFormat`\> |

#### Returns

`Record`<`string`, `OutputFormat`\>

#### Defined in

[vite/src/types.ts:56](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L56)

___

### extendTransforms

▸ `Optional` **extendTransforms**(`builtins`): `TransformFactory`<`Record`<`string`, `unknown`\>\>[]

You can use this option to extend the builtin list of import transforms.
This list will be merged with the builtin transforms before applying them to the input image.

**`default`** []

#### Parameters

| Name | Type |
| :------ | :------ |
| `builtins` | `TransformFactory`<`Record`<`string`, `unknown`\>\>[] |

#### Returns

`TransformFactory`<`Record`<`string`, `unknown`\>\>[]

#### Defined in

[vite/src/types.ts:49](https://github.com/JonasKruckenberg/imagetools/blob/a033017/packages/vite/src/types.ts#L49)
