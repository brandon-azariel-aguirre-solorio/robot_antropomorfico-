using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Interfaz_brazo_robot
{
    public partial class Interfaz_principal : Form
    {
        public int Leer =1;
        public int op = 1;
        public Interfaz_principal()
        {
            InitializeComponent();
        }

        private void iconButton_Cm_Click(object sender, EventArgs e)
        {
            abrirformulario(new Control_manual());
        }
        private void abrirformulario(object formabrir)
        {
            if(this.panel_central.Controls.Count> 0)
            {
                this.panel_central.Controls.RemoveAt(0);
            }
            Form form = formabrir as Form;
            form.TopLevel = false;
            form.Dock = DockStyle.Fill;
            this.panel_central.Controls.Add(form);
            this.panel_central.Tag = form;
            form.Show();
            
        }

        private void iconButton_configuracion_Click(object sender, EventArgs e)
        {
            abrirformulario(new Configuracion());
        }

        private void Interfaz_principal_Load(object sender, EventArgs e)
        {
            abrirformulario(new presentacion());
            seleccionardatos();
        }

        private void panel1_Paint(object sender, PaintEventArgs e)
        {

        }

        private void iconButton_pintar_Click(object sender, EventArgs e)
        {
            abrirformulario(new Automatico());
        }

        private void iconButton_consulta_Click(object sender, EventArgs e)
        {
            abrirformulario(new Consulta());
        }

        private void iconButton1_Click(object sender, EventArgs e)

        {
            abrirformulario(new Controlwifi());
            timer1.Start();
        }


        private void iconButton_close_Click(object sender, EventArgs e)
        {
          
            label_proceso.Text = "Finalizado";
            label_estado.Text = "Desconectado";
            string connectionString = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";

            string query = "UPDATE estado SET Estado_conexion = '" + label_estado.Text + "', opccion = '" + "1" + "', Proceso = '" + label_proceso.Text + "' WHERE " +
              "ID = " + "1";
            //Realizamos la conexion a la base de datos
            MySqlConnection databaseConnection = new MySqlConnection(connectionString);
            MySqlCommand commandDatabase = new MySqlCommand(query, databaseConnection);
            commandDatabase.CommandTimeout = 60; //tiempo maximo para cerrar la conexion
            try
            {
                databaseConnection.Open();
                MySqlDataReader reader = commandDatabase.ExecuteReader();
                //MessageBox.Show("Conectado", "Conectar wifi");
                
                databaseConnection.Close();


            }
            catch (Exception error)
            {
                MessageBox.Show(error.ToString());
            }
            this.Close();
           
            
        }

        private void iconButton_minus_Click(object sender, EventArgs e)
        {
            WindowState = FormWindowState.Minimized;
        }

        private void panel_central_Paint(object sender, PaintEventArgs e)
        {

        }

        private void label5_Click(object sender, EventArgs e)
        {

        }
        public void seleccionardatos()
        {

                string connectionString1 = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";
                string query1 = "SELECT * FROM estado WHERE ID = 1";
                //string query1 = "SELECT * FROM estado";
                MySqlConnection databaseConnection1 = new MySqlConnection(connectionString1);
                MySqlCommand commandDatabase1 = new MySqlCommand(query1, databaseConnection1);
                commandDatabase1.CommandTimeout = 60;
                try
                {
                    databaseConnection1.Open();
                    MySqlDataReader reader = commandDatabase1.ExecuteReader();
                    if (reader.Read())
                    {

                        label_proseso.Text = reader["Proceso"].ToString();
                        label2.Text = reader["Estado_conexion"].ToString();
                        label3.Text = reader["opccion"].ToString();
                    }

                }
                catch (Exception error)
                {
                    MessageBox.Show(error.ToString());
                }
            
            
        }
        private void timer1_Tick(object sender, EventArgs e)
        {
            op = int.Parse(label3.Text);
            if (op==1)
            {
                Leer = 1;
                consultar.iniciar = "1";
                seleccionardatos();
            }
            else
            {
                Leer = 0;
                consultar.iniciar = "0";
            }
            
          
        }

        private void label2_Click(object sender, EventArgs e)
        {

        }
    }
}
