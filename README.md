# Soluções para Gerenciamento em uma Loja de Eletrônicos

class Produto:
    def __init__(self, nome, preco, quantidade):
        self.nome = nome
        self.preco = preco
        self.quantidade = quantidade


class SistemaEstoque:
    def __init__(self):
        self.estoque = {}
        self.vendas = []

    def adicionar_produto(self):
        nome = input("Nome do produto: ")

        if nome in self.estoque:
            print(f"Produto já cadastrado!")
            return

        preco = float(input("Preço (R$): "))
        quantidade = int(input("Quantidade: "))

        self.estoque[nome] = Produto(nome, preco, quantidade)
        print("Produto adicionado com sucesso!")

    def atualizar_produto(self):
        nome = input("Nome do produto a atualizar: ")

        if nome not in self.estoque:
            print("Produto não encontrado!")
            return

        preco = float(input("Novo preço (R$): "))
        quantidade = int(input("Nova quantidade: "))

        self.estoque[nome].preco = preco
        self.estoque[nome].quantidade = quantidade
        print("Produto atualizado com sucesso!")

    def excluir_produto(self):
        nome = input("Nome do produto a excluir: ")

        if nome not in self.estoque:
            print("Produto não encontrado!")
            return

        del self.estoque[nome]
        print("Produto excluído com sucesso!")

    def visualizar_estoque(self):
        if not self.estoque:
            print("Estoque vazio.")
            return

        for produto in self.estoque.values():
            print(
                f"Produto: {produto.nome} | "
                f"Preço: R${produto.preco} | "
                f"Quantidade: {produto.quantidade}"
            )


def menu():
    sistema = SistemaEstoque()

    while True:
        print("\n=== CONTROLE DE ESTOQUE ===")
        print("1 - Adicionar produto")
        print("2 - Atualizar produto")
        print("3 - Visualizar estoque")
        print("4 - Excluir produto")
        print("5 - Sair")

        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            sistema.adicionar_produto()

        elif opcao == "2":
            sistema.atualizar_produto()

        elif opcao == "3":
            sistema.visualizar_estoque()

        elif opcao == "4":
            sistema.excluir_produto()

        elif opcao == "5":
            print("Saindo do sistema...")
            break

        else:
            print("Opção inválida!")


menu()
