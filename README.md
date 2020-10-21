# The-Cashier_Apps
Aplikasi kasir untuk mendata barang atau jasa yang dibeli oleh pembeli.

Disini menjadi pusat proses dimana jendela akan menghubungi class calculator untuk mengambil listbox melalui perintah getListItem()

public MainWindow()
        {
            InitializeComponent();
            calculator = new Calculator();
            ListBoxItem.ItemsSource = calculator.getListItem();
        }

Lalu setelah kasir menginputkan data setelah menekan tombol button, maka akan diproses melalui class item dan akan dikirimkan kepada class calculator untuk dimasukkan kedalam listbox yang akan ditampilkan oleh jendela.

        private void AddButton_Click_1(object sender, RoutedEventArgs e)
        {
            string title = NameBox.Text;
            int jumlah = Convert.ToInt32(QuantityBox.Text);
            string type = TypeComboBox.Text;
            double price = Convert.ToDouble(PriceBox.Text);

            Item item = new Item(new Random().Next(), title, jumlah, type, price);
            calculator.AddItem(item);
            double total = calculator.getTotal();

            TotalBox.Content = String.Format("RP. {0}", total);

            ListBoxItem.Items.Refresh();
        }

Untuk Single Responsibility berada pada codingan berikut. Yaitu proses dimana class tersebut akan menambahkan item yang dimasukkan oleh kasir dan ditampilkan dalam list serta menghitung total harga dari pembelian.
