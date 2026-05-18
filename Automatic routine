using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Interfaz_brazo_robot
{
    public partial class Automatico : Form
    {
        int tiempo = 4200;
        int tiempocorto = 1500;
        public Automatico()
        {
            InitializeComponent();
        }
        public void limpiar()
        {
            comboBox_color.Text = "";
            comboBox_veiculo.Text = "";
        }
        public void llenarbase()
        {
            if (comboBox_color.Text != "" && comboBox_veiculo.Text != "")
            {
                //Cadena de Conexion 
                string connectionString = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";
                string query = "INSERT INTO historial (ID, Veiculo, Color,Fecha) VALUES(NULL, '" + comboBox_veiculo.Text + "', '" + comboBox_color.Text + "', '" + label_fecha.Text + "');";

                //Realizamos la conexion a la base de datos
                MySqlConnection databaseConnection = new MySqlConnection(connectionString);
                MySqlCommand commandDatabase = new MySqlCommand(query, databaseConnection);
                commandDatabase.CommandTimeout = 60; //tiempo maximo para cerrar la conexion
                try
                {
                    databaseConnection.Open();
                    MySqlDataReader reader = commandDatabase.ExecuteReader();
                    databaseConnection.Close();

                    limpiar();
                }
                catch (Exception error)
                {
                    MessageBox.Show(error.ToString());
                }
            }
            else
            {
                MessageBox.Show("Faltan datos para el movimiento", "ERROR");

            }
        }
        
        public void rutina()
        {
            serialPort1.PortName = label_puerto.Text;
            serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
            serialPort1.Open();
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("10 " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("10 " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("0  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "c +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("10 " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("10 " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("10 " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("10 " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("10 " + "a -");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "c +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "a +");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u - L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("0  " + "o +");
            serialPort1.Close();
            MessageBox.Show("finalizado con exito");
        }

        public void rutinacorta()
        {
            serialPort1.PortName = label_puerto.Text;
            serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
            serialPort1.Open();
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("8  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("8  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("0  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "a +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("8  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("8  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("8  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("8  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("0  " + "c +");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u - L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("2  " + "a -");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "o +");
            serialPort1.Close();
        }

        private void iconButton2_Click(object sender, EventArgs e)
        {
            llenarbase();
            rutinacorta();

        }

        private void Automatico_Load(object sender, EventArgs e)
        {
            label_fecha.Text = DateTime.UtcNow.ToString("MM-dd-yyyy");
            string connectionString = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";
            string query = "SELECT * FROM conexion WHERE ID = 1";
            MySqlConnection databaseConnection = new MySqlConnection(connectionString);
            MySqlCommand commandDatabase = new MySqlCommand(query, databaseConnection);
            commandDatabase.CommandTimeout = 60;
            try
            {
                databaseConnection.Open();
                MySqlDataReader reader = commandDatabase.ExecuteReader();
                if (reader.Read())
                {

                    label_puerto.Text = reader["Puerto"].ToString();
                    label_baud.Text = reader["Baud_rate"].ToString();
                }
            }
            catch (Exception error)
            {
                MessageBox.Show(error.ToString());
            }
        }
    }
}
