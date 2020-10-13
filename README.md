# Base-de-datos-final-
Base de datos final
private void buscar()
        {
            string Connect = "datasource=localhost;port=3306;username=root;password=;database=db;";
            string query = "SELECT * FROM botones where id='" + textBox4.Text + "' ";
            MySqlConnection databaseConnection = new MySqlConnection(Connect);
            MySqlCommand commandDatabase = new MySqlCommand(query, databaseConnection);
            commandDatabase.CommandTimeout = 60;
            MySqlDataReader reader;


            try
            {
                databaseConnection.Open();
                reader = commandDatabase.ExecuteReader();
                if (reader.HasRows)
                {
                    listView1.Items.Clear();
                    while (reader.Read())
                    {
                        string[] row = { reader.GetString(0), reader.GetString(1), reader.GetString(2), reader.GetString(3) };
                        // var ListViewItems = new ListViewItem(row);
                        textBox1.Text = row[1];
                        textBox2.Text = row[2];
                        textBox3.Text = row[3];
                    }

                }
                else
                {
                    Console.WriteLine("No se encontro nada");
                }
                databaseConnection.Close();
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }
        }
