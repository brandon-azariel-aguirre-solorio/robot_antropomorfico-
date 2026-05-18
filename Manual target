using MySql.Data.MySqlClient;
using System;
using System.Data.SqlClient;
using System.Windows.Forms;
using System.Windows.Media.Media3D;

namespace Interfaz_brazo_robot
{
   
    public partial class Control_manual : Form
    {
        
        MySqlConnection cnn;
        MySqlCommand cmd;
        MySqlDataReader dr;
        int giro = 1;
        bool estado = false;
        public Control_manual()
        {
            InitializeComponent();
            cnn = new MySqlConnection("datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;");
        }
        private void label2_Click(object sender, EventArgs e)
        {

        }

        public void limipar()
        {
            actualizar();
            comboBox1.Text = "";
            textBox_angulo.Text = "";
        }
        public void llenar_posicion()
        {
        
            if (comboBox1.Text != "" && textBox_angulo.Text != "")
            {
                //Cadena de Conexion 
                string connectionString = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";
                string query = "INSERT INTO posiciones (ID, Eslabon, Posicion_grados,Sentido_de_giro) VALUES(NULL, '" + comboBox1.Text + "', '" + textBox_angulo.Text + "', '" + label_a.Text + "');";

                //Realizamos la conexion a la base de datos
                MySqlConnection databaseConnection = new MySqlConnection(connectionString);
                MySqlCommand commandDatabase = new MySqlCommand(query, databaseConnection);
                commandDatabase.CommandTimeout = 60; //tiempo maximo para cerrar la conexion
                try
                {
                    databaseConnection.Open();
                    MySqlDataReader reader = commandDatabase.ExecuteReader();
                    databaseConnection.Close();
                    actualizar();
                    limipar();
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
        private void button_emv_Click(object sender, EventArgs e)
        {
            
            
                      
        }

        private void textBox_angulo_TextChanged(object sender, EventArgs e)
        {
           
        }

        private void label3_Click(object sender, EventArgs e)
        {

        }

        private void comboBox1_SelectedIndexChanged(object sender, EventArgs e)
        {
            if (comboBox1.Text == "Base")
            {
                label_nota.Text = "Nota: El angulo de movimiento no puede sobrepasar los 90° hacia delante y hacia atras";
            }
            else if (comboBox1.Text == "Brazo")
            {
                label_nota.Text = "Nota: El angulo de movimiento no puede sobrepasar los 30° hacia abajo y 50° hacia arriba";

            }
            else if (comboBox1.Text == "Aereografo")
            {
                label_nota.Text = "Nota: El angulo de movimiento no puede sobrepasar los 60° hacia delante y hacia atras";
            }
        }
        public void actualizar()
        {
            //cnn.Open();
            //cmd = new MySqlCommand("SELECT * FROM posiciones WHERE  Eslabon = @Eslabon", cnn);
            //cmd.Parameters.AddWithValue("@Eslabon", comboBox1.Text);
            //MySqlDataReader registro = cmd.ExecuteReader();
            //if (registro.Read())
            //{
            //    label_angulo.Text = registro["Posicion_grados"].ToString();
            //    label_componente.Text = registro["Eslabon"].ToString();

            //}
            //cnn.Close();
        }
        private void textBox_angulo_KeyPress(object sender, KeyPressEventArgs e)
        {
             
        }

        private void Control_manual_Load(object sender, EventArgs e)
        {
            
            actualizar();
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
            }catch (Exception error)
            {
                MessageBox.Show(error.ToString());
            }

            if (estado == true)
            {
                giro = 1;
                estado = false;
                iconButton1.IconChar = FontAwesome.Sharp.IconChar.ArrowRotateBackward;
                label_a.Text = "Antihorario";
            }
            else if (estado == false)
            {
                giro = -1;
                estado = true;
                iconButton1.IconChar = FontAwesome.Sharp.IconChar.ArrowRightRotate;
                label_a.Text = "Horario";
            }

        }

        private void iconButton1_Click(object sender, EventArgs e)
        {
            
            if (estado==true)
            {
                giro = 1;
                estado=false;
                iconButton1.IconChar =  FontAwesome.Sharp.IconChar.ArrowRotateBackward;
                label_a.Text = "Antihorario";
            }
            else if (estado == false)
            {
                giro = -1;
                estado=true;
                iconButton1.IconChar = FontAwesome.Sharp.IconChar.ArrowRightRotate;
                label_a.Text = "Horario";
            }
        }

        private void iconButton2_Click(object sender, EventArgs e)
        {
            if (textBox_angulo.Text != "")
            {
                int angulo = int.Parse(textBox_angulo.Text);
                angulo = angulo * giro;
                labelfa.Text = angulo.ToString();

                if (angulo < 99 && angulo >= 0)
                {
                    if (comboBox1.Text == "Base")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + " b +");
                        serialPort1.Close();
                        llenar_posicion();
                        //MessageBox.Show("Enviado preparando movimiento ", "Enviar dato");
                    }
                    else if (comboBox1.Text == "Brazo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + " c +");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else if (comboBox1.Text == "Aereografo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + " a +");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else
                    {
                        MessageBox.Show("El angulo sobrepaso el limite de movimiento", "Enviar angulo");
                    }

                }
                else if (angulo > 100)
                {
                    if (comboBox1.Text == "Base")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + "b +");
                        serialPort1.Close();
                        llenar_posicion();
                        //MessageBox.Show("Enviado preparando movimiento ", "Enviar dato");
                    }
                    else if (comboBox1.Text == "Brazo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + "c +");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else if (comboBox1.Text == "Aereografo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + "a +");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else
                    {
                        MessageBox.Show("El angulo sobrepaso el limite de movimiento", "Error");
                    }

                }
                else if (angulo < 0 && angulo > -100)
                {
                    if (comboBox1.Text == "Base")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + " b -");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else if (comboBox1.Text == "Brazo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + " c -");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else if (comboBox1.Text == "Aereografo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + " a -");
                        serialPort1.Close();
                        llenar_posicion();

                    }

                }
                else if (angulo < -99)
                {
                    if (comboBox1.Text == "Base")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + "b -");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else if (comboBox1.Text == "Brazo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + "c -");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else if (comboBox1.Text == "Aereografo")
                    {
                        label_posicion.Text = comboBox1.Text;
                        label_angulo.Text = textBox_angulo.Text;
                        serialPort1.PortName = label_puerto.Text;
                        serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
                        serialPort1.Open();
                        serialPort1.Write(textBox_angulo.Text + "a -");
                        serialPort1.Close();
                        llenar_posicion();

                    }
                    else
                    {
                        MessageBox.Show("El angulo sobrepaso el limite de movimiento", "Error");
                    }

                }
            }

        }
    }
}
