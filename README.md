A clever capsulation of View Holder pattern in Android:

    public class ItemsAdapter extends ArrayAdapter<Item> {
      private final static int resource = R.layout.list_home_items;
      private Context context;
      
      public ItemsAdapter(Context _context, List<Item> objects) {
        super(_context, resource, objects);
        context = _context;
      }
      
      @Override
      public View getView(int position, View convertView, ViewGroup parent){
        ViewHolder holder = ViewHolder.newInstance(context, convertView, parent, resource);
        Item item = getItem(position);
        holder.setText(R.id.item_title, item.title);
        holder.setImageUrl(context, R.id.item_image, item.large_image);
        return holder.convertView;
      }
    }