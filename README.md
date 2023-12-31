# coco

koa & fastify alternative

```typescript
import { App, Router } from "@w72/coco";
import { z } from "zod";

const app = new App();

const router = new Router();

router.get(
  "/",
  {
    query: z.object({ test: z.optional(z.string()) }),
  },
  (ctx) => ({ hello: `hello ${ctx.query.test}` })
);

router.get(
  "/test/:id",
  {
    query: z.object({ test: z.optional(z.string()) }),
    params: z.object({ id: z.coerce.number() }),
  },
  (ctx) => ({ hello: `hello ${ctx.params.id} ${ctx.query.test}` })
);

app.use(router.middleware());
app.listen(8080);
app.log.info("Server starting at http://localhost:8080");
```
