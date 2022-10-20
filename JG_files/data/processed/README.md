Capstone_MLE9
==============================

# Processed Data

# create reduced dataset without columns that provide no information.
# dropping also switch  id and port id

reduced_df = raw_df[[#'Switch ID', 
                        #'Port Number', 
                        'Received Packets', 
                        'Received Bytes', 
                        'Sent Bytes', 
                        'Sent Packets', 
                        'Port alive Duration (S)',
                        #'Packets Rx Dropped', 
                        #'Packets Tx Dropped', 
                        #'Packets Rx Errors',
                        #'Packets Tx Errors', 
                        'Delta Received Packets', 
                        'Delta Received Bytes',
                        'Delta Sent Bytes', 
                        'Delta Sent Packets',
                        'Delta Port alive Duration (S)', 
                        #'Delta Packets Rx Dropped',
                        #' Delta Packets Tx Dropped', 
                        #'Delta Packets Rx Errors',
                        #'Delta Packets Tx Errors', 
                        'Connection Point', 
                        'Total Load/Rate',
                        'Total Load/Latest', 
                        'Unknown Load/Rate', 
                        'Unknown Load/Latest',
                        'Latest bytes counter', 
                        #'is_valid', 
                        #'Table ID', 
                        'Active Flow Entries',
                        'Packets Looked Up', 
                        'Packets Matched', 
                        #'Max Size', 
                        'Label',
                        'Binary Label']]




labels_binlab = labels_binlab.replace(to_replace= ["Attack", "Normal"], value= [1 , 0])
labels_labcat = labels_labcat.replace(to_replace= ['Blackhole', 'Diversion', 'Normal', 'Overflow', 'PortScan', 'TCP-SYN'], value= [1 , 2, 3, 4, 5, 6])

# separate data in train and test sets, using binlab labels.
X_train_bin, X_test_bin, y_train_bin, y_test_bin = train_test_split(r_features,labels_binlab, random_state= 0 , test_size= 0.2)
                      