
# 🧩 `afterSave`: Executando ações após o salvamento de dados

O `afterSave` é uma função de **ciclo de vida** que permite executar uma lógica imediatamente após o salvamento de um formulário ou entidade. Ele é útil quando precisamos realizar ações **logo após os dados terem sido persistidos**, como atualizar a interface, exibir mensagens ou preparar o próximo passo de um fluxo.

## 🛠️ Como funciona

A função `afterSave` é chamada automaticamente **depois que o salvamento é concluído com sucesso**. Isso permite que você reaja ao salvamento de forma síncrona ou assíncrona, executando tarefas adicionais com os dados já persistidos.

## 📌 Exemplo de uso prático

Imagine que você está construindo um formulário de **agendamento**, e ele é dividido em **etapas (stepper)**. Após salvar os dados da primeira etapa, você quer imediatamente mostrar os dados salvos para o usuário conferir na próxima etapa. Para isso, você pode usar o `afterSave` da seguinte forma:

```ts
afterSave: async (savedData) => {
  // Atualiza o campo que será usado na próxima etapa
  form.setFieldValue('repeter', savedData.repeter);

  // Avança para a próxima etapa do fluxo
  goToStep(2);
}
```

Neste exemplo:
- Após salvar os dados, o campo `repeter` é atualizado com os dados recém-salvos.
- Em seguida, o fluxo de etapas avança para o segundo passo, onde os dados já aparecem atualizados para o usuário.

## 🎯 Outros usos comuns

Você também pode usar o `afterSave` para:

- Exibir um alerta ou toast de sucesso:
  ```ts
  afterSave: () => {
    alert('Agendamento salvo com sucesso!');
  }
  ```

- Fazer um `console.log` para depuração:
  ```ts
  afterSave: (data) => {
    console.log('Dados salvos:', data);
  }
  ```

- Disparar uma nova requisição com base nos dados salvos.

## ✅ Resumo

O `afterSave` é um ponto de extensão simples, mas poderoso, ideal para automatizar ações após o salvamento de dados. Ele ajuda a melhorar a experiência do usuário e a manter a interface sempre sincronizada com o backend.
