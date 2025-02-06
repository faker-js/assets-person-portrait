# Faker Assets for Person Portraits

This repository is only for hosting images for [`faker.image.personPortrait()`](https://fakerjs.dev/api/image.html#personportrait). \
Please report issues to the [main faker repo](https://github.com/faker-js/faker). \
PRs will be rejected.

Please access the assets via CDN, for example

https://cdn.jsdelivr.net/gh/faker-js/assets-person-portrait/female/512/42.jpg

## Repo Structure

```txt
/SEX/SIZE/INDEX.jpg
/{male,female}/{32,64,128,256,512}/{0...99}.jpg
```

## Re-Generating New Images

The basic prompt used for Stable Diffusion 3 was:

`profile picture of a ${age}-year-old ${type} from ${country}`

You can use the data in the male/metadata and female/metadata to regenerate images. You can run a model locally, or use a service like Replicate using https://github.com/replicate/replicate-javascript. You will need a Replicate API key, and expect it will cost approximately 	[$0.035 per image](https://replicate.com/pricing) to generate.

```js
import Replicate from "replicate";
const replicate = new Replicate({
    auth: process.env.REPLICATE_API_TOKEN,
});
const metadata = JSON.parse(fs.readFileSync("female/metadata/42.json"))
const input = metadata.parameters;
const output = await replicate.run(metadata.model, {
    input
});
console.log(output);
```
