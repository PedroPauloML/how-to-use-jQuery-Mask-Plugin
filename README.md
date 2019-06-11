# How to use jQuery Mask Plugin

A simple example how to use [jQuery Mask Plugin](https://igorescobar.github.io/jQuery-Mask-Plugin/).

## Prerequisites

In this example was used the CDNjs [jQuery Mask Plugin v1.14.15](https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.15/jquery.mask.js) and [jQuery 3.3.1](https://code.jquery.com/jquery-3.3.1.slim.min.js).
So, put the scripts CDNjs before close the tag body.
```html
<body>
  ...
  <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.15/jquery.mask.js"></script>
</body>
```

## Getting started

Type a HTML markup to apply masks:
```html
<body>
  <input type="text" id="cpf" name="cpf" class="cpfMask" placeholder="Type your CPF" />
  <input type="text" id="cnpj" name="cnpj" class="cnpjMask" placeholder="Type your CNPJ" />
  <input type="text" id="cpfOrCnpj" name="cpfOrCnpj" class="cpfCnpjMask" placeholder="Type your CPF or CNPJ" />
  ...
</body>
```

After create the script to call mask function:
```html
<body>
  ...
  <script>
    $(document).ready(function() {
        // Setting all elements with class ".cpfMask" to use the mask of CPF
      $('.cpfMask').mask('000.000.000-00')
      // Setting all elements with class ".cnpjMask" to use the mask of CNPJ
      $('.cnpjMask').mask('00.000.000/0000-00')

      // Option to choose which mask use
      const cpf_cnpj_options = {
        onKeyPress: (cpf_cnpj, e, field, options) => {
          // Put CPF mask with one more charecter to permit the change to CNPJ mask
          const masks = ['000.000.000-000', '00.000.000/0000-00']
          // Choosing which mask use based on input length
          const mask  = cpf_cnpj.length > 14 ? masks[1] : masks[0]
          // Applying choose
          $('.cpfCnpjMask').mask(mask, options)
        }
      }

      // Setting all elements with class ".cpfCnpjMask" to use the mask of CPF/CPNJ
      // passing options to toggle between CPF and CNPJ mask
      $('.cpfCnpjMask').mask('00.000.000/0000-00', cpf_cnpj_options)
    });
  </script>
</body>
```

Your body tag should stay like this:

```html
<body>
  <input type="text" id="cpf" name="cpf" class="cpfMask" placeholder="Type your CPF" />
  <input type="text" id="cnpj" name="cnpj" class="cnpjMask" placeholder="Type your CNPJ" />
  <input type="text" id="cpfOrCnpj" name="cpfOrCnpj" class="cpfCnpjMask" placeholder="Type your CPF or CNPJ" />

  <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.15/jquery.mask.js"></script>
  <script>
    $(document).ready(function() {
        // Setting all elements with class ".cpfMask" to use the mask of CPF
      $('.cpfMask').mask('000.000.000-00')
      // Setting all elements with class ".cnpjMask" to use the mask of CNPJ
      $('.cnpjMask').mask('00.000.000/0000-00')

      // Option to choose which mask use
      const cpf_cnpj_options = {
        onKeyPress: (cpf_cnpj, e, field, options) => {
          // Put CPF mask with one more charecter to permit the change to CNPJ mask
          const masks = ['000.000.000-000', '00.000.000/0000-00']
          // Choosing which mask use based on input length
          const mask  = cpf_cnpj.length > 14 ? masks[1] : masks[0]
          // Applying choose
          $('.cpfCnpjMask').mask(mask, options)
        }
      }

      // Setting all elements with class ".cpfCnpjMask" to use the mask of CPF/CPNJ
      // passing options to toggle between CPF and CNPJ mask
      $('.cpfCnpjMask').mask('00.000.000/0000-00', cpf_cnpj_options)
    });
  </script>
</body>
```

Now, all is ready! Just that!

Any doubt on building example? See the [example HTML](#).