# Refactoring
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace classwork
{
    public partial class RowImporting : Form
    {
        DataTable dtAllItems = new DataTable();
        DataTable dtSelectedItems = new DataTable();
        DataTable dtResult = new DataTable();
        public RowImporting()
        {
            InitializeComponent();
        }
        private void FillData()
        {
            dtAllItems.Columns.Add("ID", typeof(int));
            dtAllItems.Columns.Add("Name");
            dtAllItems.Columns.Add("Experties");
            dtAllItems.Columns.Add("Phone");


            dtSelectedItems.Columns.Add("ID", typeof(int));
            dtSelectedItems.Columns.Add("Name");
            dtSelectedItems.Columns.Add("Experties");
            dtSelectedItems.Columns.Add("Phone");

            dtAllItems.Rows.Add(10, "Hira Rehman", "abcxyz", "03335858587");
            dtAllItems.Rows.Add(11, "Asma Bashir", "Stay Awake", "033358456587");
            dtAllItems.Rows.Add(12, "Isha Kiyani", "abcxyz", "0333585897");
            dtAllItems.Rows.Add(13, "Izza Rehman", "asdasd", "03455858587");
            dtAllItems.Rows.Add(14, "Laiba Riaz", "Attendance preferrence", "03548975878");
            dtAllItems.Rows.Add(15, "Muhammad Awais Umer", "abcxyz", "03325858587");
            dtAllItems.Rows.Add(16, "Hammad Ullah Inayat", "Stay Awake", "033358456587");
            dtAllItems.Rows.Add(17, "Uzair Abbas", "abcxyz", "03333585897");
            dtAllItems.Rows.Add(18, "Ch Muhammad Zryab Waheed", "asdasd", "03455858587");
            dtAllItems.Rows.Add(19, "Muhammad Hammad", "Attendance Specialist", "03458975878");
            dtAllItems.Rows.Add(20, "Muhammad Nabeel", "abcxyz", "03335858587");
            dtAllItems.Rows.Add(21, "Muzammil Bashir", "Stay Awake", "033358456587");
            dtAllItems.Rows.Add(22, "Muhammad Arif", "abcxyz", "0333585897");
            dtAllItems.Rows.Add(23, "Adnan Rehman", "asdasd", "03455859887");
            dtAllItems.Rows.Add(24, "Saleem Aftab", "Attendance Specialist", "035485975878");
        }
        private void listBox1_SelectedIndexChanged(object sender, EventArgs e)
        {
          
        }

        private void RowImporting_Load(object sender, EventArgs e)
        {
            FillData();

            listBox1.DataSource = dtAllItems;
            listBox1.DisplayMember = "Name";

            listBox2.DataSource = dtSelectedItems;
            listBox2.DisplayMember = "Name";
        }

        private void button1_Click(object sender, EventArgs e)
        {
                if (listBox1.Items.Count > 0)
                {
                    dtSelectedItems.ImportRow(dtAllItems.Rows[listBox1.SelectedIndex]);
                    dtAllItems.Rows[listBox1.SelectedIndex].Delete();
                }
        }

        private void button2_Click(object sender, EventArgs e)
        {
            if (listBox2.Items.Count > 0)
            {
                dtAllItems.ImportRow(dtSelectedItems.Rows[listBox2.SelectedIndex]);
                dtSelectedItems.Rows[listBox2.SelectedIndex].Delete();
            }
        }

        private void listBox2_SelectedIndexChanged(object sender, EventArgs e)
        {
            
        }

        private void button3_Click(object sender, EventArgs e)
        {
            for (int i = 0; i <= dtAllItems.Rows.Count; i=1)
            {
                if (listBox1.Items.Count > 0)
                {
                    dtSelectedItems.ImportRow(dtAllItems.Rows[listBox1.SelectedIndex]);
                    dtAllItems.Rows[listBox1.SelectedIndex].Delete();
                }
            }
        }

        private void listBox2_SelectedIndexChanged_1(object sender, EventArgs e)
        {

        }

        private void button4_Click(object sender, EventArgs e)
        {
                if (listBox2.Items.Count > 0)
                {
                    dtAllItems.ImportRow(dtSelectedItems.Rows[listBox2.SelectedIndex]);
                    dtSelectedItems.Rows[listBox2.SelectedIndex].Delete();
                    button4_Click(sender, e);
            }   
        }
}
