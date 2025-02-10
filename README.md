# Faker Assets for Person Portraits

This repository is only for hosting images for [`faker.image.personPortrait()`](https://fakerjs.dev/api/image.html#personportrait).

> [!IMPORTANT]
> The [images](https://faker-js.github.io/assets-person-portrait/) in this repository are generated by AI. \
> If you think one of the image resembels you too closely and would like to have it changed, please let us know.

Please report any issues and feature requests to the [main faker repo](https://github.com/faker-js/faker). \
This repostory does not accept PRs to ensure we do not exceed GitHubs file, size and transfer limits.

Please access the assets via CDN:

https://cdn.jsdelivr.net/gh/faker-js/assets-person-portrait/female/512/42.jpg

## Repo Structure

```txt
/SEX/SIZE/INDEX.jpg
/{male,female}/{32,64,128,256,512}/{0...99}.jpg
```

## Re-Generating New Images

The basic prompt used for Stable Diffusion 3 was:

`profile picture of a ${age}-year-old ${type} from ${country}`

You can use the data in the male/metadata and female/metadata to regenerate images. You can run a model locally, or use a service like Replicate using https://github.com/replicate/replicate-javascript. You will need a Replicate API key, and expect it will cost approximately [$0.035 per image](https://replicate.com/pricing) to generate.

```js
import Replicate from "replicate";
const replicate = new Replicate({
  auth: process.env.REPLICATE_API_TOKEN,
});
const metadata = JSON.parse(fs.readFileSync("female/metadata/42.json"));
const input = metadata.parameters;
const output = await replicate.run(metadata.model, {
  input,
});
console.log(output);
```
