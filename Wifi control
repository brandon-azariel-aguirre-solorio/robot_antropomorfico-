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
using AForge.Imaging;
using AForge.Imaging.Filters;
using AForge;
using AForge.Video;
using AForge.Video.DirectShow;
using static System.Net.Mime.MediaTypeNames;
using System.Drawing.Imaging;
using System.Diagnostics.Tracing;
using System.Threading;

namespace Interfaz_brazo_robot
{
    public partial class Controlwifi : Form
    {
        int tiempo = 3800;//3800
        int tiempocorto = 2500;
        int R = 0, G = 0, B = 0;
        public FilterInfoCollection VideoCaptureDevices;
        public VideoCaptureDevice videofinal;
        int valuecolor = 0;
        int objeto = 0;
        int cosas = 0;
        string escribir = "";
        int ler =0;
        public Controlwifi()
        {
            InitializeComponent();
        }
        public void entrar()
        {
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
        public void rutinacrv()
        {
            label5.Text = "Proceso de pintura iniciado";
            serialPort1.PortName = label_puerto.Text;
            serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
            serialPort1.Open();
            Thread.Sleep(tiempocorto);
            serialPort1.Write("7  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("7  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("10 " + "a +");
            Thread.Sleep(tiempo);
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
            serialPort1.Write("5  " + "c +");
            Thread.Sleep(2000);
            serialPort1.Write("10 " + "a -");
            Thread.Sleep(3500);
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("8  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("8  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u - L");
            Thread.Sleep(2000);
            serialPort1.Write("5  " + "c -");
            Thread.Sleep(3000);
            serialPort1.Write("0  " + "o +");
            serialPort1.Close();
            label5.Text = "Robot Pintor Control Wifi";
            label_proseso.Text = "Finalizado";
            label_Estado.Text = "Conectado";
            actualizarbase();
            consultar.iniciar = "1";
            timer1.Start();
        }
        public void rutinacrvespera()
        {
            label5.Text = "Proceso de pintura iniciado";
            serialPort1.PortName = label_puerto.Text;
            serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
            serialPort1.Open();
            serialPort1.Write("7  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("7  " + "b -");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("5  " + "u + R");
            serialPort1.Close();
            Thread.Sleep(tiempocorto);
            serialPort1.Open();
            serialPort1.Write("0  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("10 " + "a +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("8  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("8  " + "b -");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("8  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("8  " + "b -");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("5  " + "u + L");
            serialPort1.Close();
            Thread.Sleep(tiempocorto);
            serialPort1.Open();
            serialPort1.Write("5  " + "c +");
            serialPort1.Close();
            Thread.Sleep(2000);
            serialPort1.Open();
            serialPort1.Write("10 " + "a -");
            serialPort1.Close();
            Thread.Sleep(3500);
            serialPort1.Open();
            serialPort1.Write("5  " + "u + R");
            serialPort1.Close();
            Thread.Sleep(tiempocorto);
            serialPort1.Open();
            serialPort1.Write("8  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("0  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("8  " + "b -");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("0  " + "b +");
            serialPort1.Close();
            Thread.Sleep(tiempo);
            serialPort1.Open();
            serialPort1.Write("5  " + "u - L");
            serialPort1.Close();
            Thread.Sleep(2000);
            serialPort1.Open();
            serialPort1.Write("5  " + "c -");
            serialPort1.Close();
            Thread.Sleep(3000);
            serialPort1.Write("0  " + "o +");

            serialPort1.Close();
            label5.Text = "Robot Pintor Control Wifi";
            label_proseso.Text = "Finalizado";
            label_Estado.Text = "Conectado";
            actualizarbase();
            consultar.iniciar = "1";
            timer1.Start();
        }
        public void rutinagtr()
        {
            label5.Text = "Proceso de pintura iniciado";
            serialPort1.PortName = label_puerto.Text;
            serialPort1.BaudRate = Convert.ToInt32(label_baud.Text);
            serialPort1.Open();
            serialPort1.Write("5  " + "u + L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("8  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("8  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "c +");
            Thread.Sleep(4500);
            serialPort1.Write("5  " + "u + R");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("0  " + "b -");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "a +");
            Thread.Sleep(tiempo);
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
            serialPort1.Write("5  " + "a -");
            Thread.Sleep(tiempo);
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
            label5.Text = "Robot Pintor Control Wifi";
            label_proseso.Text = "Finalizado";
            label_Estado.Text = "Conectado";
            actualizarbase();
            consultar.iniciar = "1";
            timer1.Start();
        }
        public void rutina_vertical()
        {
            label5.Text = "Proceso de pintura iniciado";
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
            serialPort1.Write("0  " + "b +");
            Thread.Sleep(tiempo);
            serialPort1.Write("5  " + "u - L");
            Thread.Sleep(tiempocorto);
            serialPort1.Write("2  " + "a -");
            Thread.Sleep(tiempo);
            serialPort1.Write("0  " + "o +");
            serialPort1.Close();
            label5.Text = "Robot Pintor Control Wifi";
            label_proseso.Text = "Finalizado";
            label_Estado.Text = "Conectado";
            actualizarbase();
            consultar.iniciar = "1";
            timer1.Start();
        }
        public void videofinal_newframe(object sender, NewFrameEventArgs eventArgs)
        {
            Bitmap image = (Bitmap)eventArgs.Frame.Clone();
            Bitmap image2 = (Bitmap)eventArgs.Frame.Clone();
            //pictureBox_camara.Image = image;
            EuclideanColorFiltering filtering = new EuclideanColorFiltering();
            filtering.CenterColor = new RGB(Color.FromArgb(R, G, B));
            filtering.Radius = 120;//100
            filtering.ApplyInPlace(image2);
            detectarobjeto(image2);

        }
        public void detectarobjeto(Bitmap carro)
        {
            BlobCounter blobCounter = new BlobCounter();
            blobCounter.MinWidth = 3;
            blobCounter.MinHeight = 3;
            blobCounter.FilterBlobs = true;
            blobCounter.ObjectsOrder = ObjectsOrder.Size;

            BitmapData objetsdata = carro.LockBits(new Rectangle(0, 0, carro.Width, carro.Height), ImageLockMode.ReadOnly, carro.PixelFormat);
            Grayscale grayscalefilter = new Grayscale(0.2125, 0.7154, 0.07221);
            //Grayscale grayscalefilter = new Grayscale(R-200, G-200, B-200);
            UnmanagedImage grayimage = grayscalefilter.Apply(new UnmanagedImage(objetsdata));
            carro.UnlockBits(objetsdata);
            blobCounter.ProcessImage(carro);
            Rectangle[] rectangles = blobCounter.GetObjectsRectangles();
            Blob[] blobs = blobCounter.GetObjectsInformation();
            pictureBox_camaracolor.Image = carro;

            foreach (Rectangle rectangle in rectangles)
            {
                cosas = 0;
                objeto = 0;
                cosas = rectangles.Length;
   
                if (rectangles.Length >= 1)
                {
                  
                    //Rectangle rectangle1 = rectangles[0];
                   // Graphics g = pictureBox_camara.CreateGraphics();
                    //using (Pen pen = new Pen(Color.FromArgb(R, G, B), 2))
                   // {
                       //g.DrawRectangle(pen, rectangle1);
                        //g.DrawString("Veiculo a pintar", new Font("Arial", 16), Brushes.Red, rectangle1);
                    //}
                    objeto = 1;

                }
                else
                {
                    objeto = 0;
                    cosas = 0;

                }
               

            }

     

        }
        public void actualizarbase()
        {
            string connectionStringa = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";
            string querya = "UPDATE estado SET Estado_conexion = '" + label_Estado.Text + "', Proceso = '" + label_proseso.Text + "' WHERE " +
              "ID = " + "1";
            //Realizamos la conexion a la base de datos
            MySqlConnection databaseConnection = new MySqlConnection(connectionStringa);
            MySqlCommand commandDatabase = new MySqlCommand(querya, databaseConnection);
            commandDatabase.CommandTimeout = 60; //tiempo maximo para cerrar la conexion
            try
            {
                databaseConnection.Open();
                MySqlDataReader reader = commandDatabase.ExecuteReader();
                databaseConnection.Close();

            }
            catch (Exception error)
            {
                MessageBox.Show(error.ToString());
            }
        }
        public void camara()
        {

            label_objetos.Text = cosas.ToString();
            actualizarobjeto();
            objeto = 0;
        }
        public void actualizarobjeto()
        {
       
           if (objeto == 1)
            {

                if (label_proseso.Text == "No se puede pintar")
                {
                    label_proseso.Text = "Listo para pintar";
                    label_detec.Text = "Detectado";
                    actualizarbase();
                }
                else if (label_proseso.Text == "Listo para pintar")
                {
                    label_detec.Text = "Detectado";
                    label_proseso.Text = "Listo para pintar";
                    label_Estado.Text = "Conectado";
                }
                else
                {
                    label_proseso.Text = "Listo para pintar";
                }
               
            }
            else if (objeto == 0)
            {
                
                if (label_proseso.Text == "Listo para pintar" )
                {
                    label_proseso.Text = "No se puede pintar";
                    label_detec.Text = "No detectado";
                    actualizarbase();
                }
                else if (label_proseso.Text == "No se puede pintar")
                {
                    label_proseso.Text = "No se puede pintar";
                    label_detec.Text = "No detectado";
                }
                else
                {  
                    label_proseso.Text = "No se puede pintar";
                    label_detec.Text = "No detectado";

                }
              

            }
            
        }

        private void timer1_Tick(object sender, EventArgs e)
        {

            label_leer.Text = consultar.iniciar;
            escribir = label_leer.Text;
            label_a.Text = escribir;    
            if (escribir == "1")
            {
                camara();
            }
            else if (escribir == "0")
            {
                entrar();
                rutinacrv();
                timer1.Stop();
            }
           


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
                    label_Estado.Text = reader["Estado_conexion"].ToString();
                }

            }
            catch (Exception error)
            {
                MessageBox.Show(error.ToString());
            }
        }
        public void sensar()
        {
            //seleccionardatos();

        }
        private void timer2_Tick_1(object sender, EventArgs e)
        {
            
        }

        private void label5_Click(object sender, EventArgs e)
        {

        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        public void cerrar()
        {
 
            string connectionString = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";

            string query = "UPDATE estado SET Estado_conexion = '" + "Desconectado" + "', opccion = '" + "1" + "', Proceso = '" + "Finalizado" + "' WHERE " +
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

        }
        private void Controlwifi_Load(object sender, EventArgs e)
        {
            VideoCaptureDevices = new FilterInfoCollection(FilterCategory.VideoInputDevice);
            foreach (FilterInfo VideoCaptureDevice in VideoCaptureDevices)
            {
                comboBox_camaras.Items.Add(VideoCaptureDevice.Name);
            }
            comboBox_camaras.SelectedIndex = 0;
            objeto = 0;
            label_proseso.Text = "Finalizado";
            label_Estado.Text = "Conectado";
            string connectionString = "datasource=127.0.0.1;port=3306;username=root;password=Password;database=robot_antropomorfico;";
            string query = "UPDATE estado SET Estado_conexion = '" + label_Estado.Text + "', Proceso = '" + label_proseso.Text + "' WHERE " +
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
                videofinal = new VideoCaptureDevice(VideoCaptureDevices[comboBox_camaras.SelectedIndex].MonikerString);
                videofinal.NewFrame += new NewFrameEventHandler(videofinal_newframe);
                videofinal.DesiredFrameRate = 20;
                videofinal.DesiredFrameSize = new Size(320, 240);//new Size(320, 240)
                videofinal.Start();
                R = 65;
                G = 235;
                B = 245;
                label_leer.Text = consultar.iniciar;
                timer1.Start();

            }
            catch (Exception error)
            {
                MessageBox.Show(error.ToString());
            }
        }
    }
    
}


