# mast-part-2


https://youtu.be/F6K3TGSYDW8 <- youtube video link


the above video is my yourube explanation video of my app and a deeper explanation of part 2 using both labs and figma

THE ABOVE IS MY REACT NATIVE CS CODE THAT HAS 8 ERRORS
import React, { useState } from 'react';
import { StyleSheet, Text, View, TextInput, Picker, Button, ScrollView, Alert } from 'react-native';

const App = () => {
  const [dishName, setDishName] = useState('');
  const [description, setDescription] = useState('');
  const [course, setCourse] = useState('Starter');
  const [price, setPrice] = useState('');
  const [menuItems, setMenuItems] = useState([]);

  const addMenuItem = () => {
    if (!dishName || !description || isNaN(parseFloat(price)) || parseFloat(price) <= 0) {
      Alert.alert("Error", "Please fill all fields correctly.");
      return;
    }

    const newItem = {
      dishName,
      description,
      course,
      price: parseFloat(price).toFixed(2),
    };

    setMenuItems([...menuItems, newItem]);

    // Clear input fields
    setDishName('');
    setDescription('');
    setPrice('');
    setCourse('Starter');
  };

  return (
    <ScrollView contentContainerStyle={styles.container}>
      <Text style={styles.header}>Menu Item App</Text>
      
      <TextInput
        style={styles.input}
        placeholder="Dish Name"
        value={dishName}
        onChangeText={setDishName}
      />
      
      <TextInput
        style={styles.input}
        placeholder="Description"
        value={description}
        onChangeText={setDescription}
      />
      
      <Picker
        selectedValue={course}
        style={styles.input}
        onValueChange={(itemValue) => setCourse(itemValue)}
      >
        <Picker.Item label="Starter" value="Starter" />
        <Picker.Item label="Main" value="Main" />
        <Picker.Item label="Dessert" value="Dessert" />
      </Picker>
      
      <TextInput
        style={styles.input}
        placeholder="Price"
        keyboardType="numeric"
        value={price}
        onChangeText={setPrice}
      />
      
      <Button title="Add Menu Item" onPress={addMenuItem} />

      <View style={styles.menuList}>
        <Text style={styles.subHeader}>Menu Items</Text>
        {menuItems.map((item, index) => (
          <View key={index} style={styles.menuItem}>
            <Text><Text style={styles.label}>Dish: </Text>{item.dishName}</Text>
            <Text><Text style={styles.label}>Description: </Text>{item.description}</Text>
            <Text><Text style={styles.label}>Course: </Text>{item.course}</Text>
            <Text><Text style={styles.label}>Price: </Text>${item.price}</Text>
          </View>
        ))}
      </View>
    </ScrollView>
  );
};

const styles = StyleSheet.create({
  container: {
    padding: 20,
    backgroundColor: '#fff',
    flexGrow: 1,
  },
  header: {
    fontSize: 24,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 20,
  },
  input: {
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 5,
    padding: 10,
    marginBottom: 10,
    width: '100%',
  },
  menuList: {
    marginTop: 20,
  },
  subHeader: {
    fontSize: 20,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  menuItem: {
    padding: 10,
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 5,
    marginBottom: 10,
  },
  label: {
    fontWeight: 'bold',
  },
});

export default App;

