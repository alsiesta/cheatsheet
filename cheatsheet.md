# Django models cheat sheet

| Model Field     | Use               | Sensible defaults                 |
|-----------------|-------------------|-----------------------------------|
| `CharField`     | Small text        | blank=False, null=False, max_length=150 |
| `TextField`     | Large text        | blank=False, null=False, max_length=150 |
| `BooleanField`  | Flags             | default=False                   |
| `DateField`     | Dates             | auto_now_add=True               |
| `DateTimeField` | Date and Time     | auto_now_add=True               |
| `EmailField`    | Small text        | blank=False, null=False         |
| `URLField`      | Small text        | blank=False, null=False         |
| `IntegerField`  | Numbers           | blank=False, null=False         |
| `SlugField`     | Slug strings      | blank=False, null=False         |
| `ImageField`    | Image uploads     | null=False                      |
| `FileField`     | File uploads      | upload_to='uploads/'            |
| `FilePathField` | File paths        | path='/path/to/'                |
