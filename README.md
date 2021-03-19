# Pagamento-Produto

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Data.SqlClient;

namespace sistemaProduto
{


    public partial class Form1 : Form
    {
        private object textoIndice;
        private object seleciona;
        private object nome_produto;
        private object data_vencimento;
        private object ocorrencia;
        private object strcon;
        private readonly object ex;

        public CommandType CommandType { get; private set; }

        public Form1()
        {
            InitializeComponent();
        }
        class Pedido
        {
            public int numPedido;
            public string nome_produto;
            public decimal valor;
            public DateTime data_vencimento;
            public string ocorrencia;
        }
        enum Ocorrencia
        {
            Estávencido,
            Estáquasevencido,
            Estáválido
        } 

        
    class Program
        {
            static void Main(string[]args)
            {
                Pedido pedido = new Pedido();

                pedido.nome_produto = 1;
                pedido.data_vencimento = DateTime.Now;
                pedido.ocorrencia = Ocorrencia as string;

                Console.WriteLine("Informações sobre este pedido: "
                    + pedido.nome_produto.ToString() 
                    + pedido.data_vencimento.ToString()
                    + pedido.valor.ToString()
                    + pedido.ocorrencia.ToString());

                Console.ReadLine();
            }
        }

        private void btnBusca_Click(object sender, EventArgs e)
        {
            int indice = Convert.ToInt32(textoIndice);
            textNumPedido.Text = object.numPedido;

            {
                string sql = "INSERT INTO PRODUTO
                        (nome_produto, data_vencimento, ocorrencia, textNumPedido, textValor)";
                        + "VALUES ('" + textNumPedido.Text + "', '" + textOcorrencia.Text + '", "'
                        + textValor.Text + "', '" + textDescProduto.Text)string v = ";";

                if {
                    SqlConnection conexao = new SqlConnection(strcon);
                    SqlCommand cmd = new SqlCommand("SELECT * FROM dbProduto", conexao);
                    {
                        CommandType = CommandType.Text;
                    };
                    try
                    {
                        conexao.Open();
                        cmd.ExecuteNonQuery();

                        {
                            int i = cmd.ExecuteNonQuery();
                            if (i > 0)
                                MessageBox.Show("Informações carregado com sucesso!!!");
                        }
                    }
                    catch (Exception ex)
                    {
                        MessageBox.Show("Erro:" + ex.ToString());
                    }
                    finally
                    {
                        conexao.Close();
                    }
                }
            }
        }
           


        private void btnDesconto_Click(object sender, EventArgs e)
            {
            MessageBox.Show("Desconto");
            }

        private void btnFinCompra_Click(object sender, EventArgs e)
        {
            MessageBox.Show("Finalizar Compra");
        }
    }

    namespace ContaReceber.Models
    {
        public enum Receber {  Aberto = 'A'}

        public abstract class Conta
        {
            public int Id { get; set; }
            public DateTime data_vencimento { get; set; }
            public decimal valor { get; set; }
            public Ocorrencia ocorrencia { get; set; }
        }
    }
}
