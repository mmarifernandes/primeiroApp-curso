import { useState } from 'react';
import { Button, StyleSheet, Text, TextInput, View } from 'react-native';

export default function NameList() {

    const [nomes, setNomes] = useState([])
    const [inputValue, setInputValue] = useState('')

    const addNomes = () => {
        if (inputValue.trim() !== '') {
            setNomes([...nomes, inputValue])
            setInputValue('')
        };
    };

    return (
        <View style={styles.container}>
            <TextInput
                style={styles.input}
                placeholder="Digite o nome"
                value={inputValue}
                onChangeText={text => setInputValue(text)}
            />
            <Button title="Adicionar" onPress={addNomes} />
            <Text style={styles.title}>Lista de nomes: </Text>
            {nomes.map((nome, index) => (
                <Text key={index} style={styles.name}> {nome} </Text>
            ))}
        </View>
    );
}

const styles = StyleSheet.create({
    container: {
        flex: 1,
        padding: 20,
        alignItems: 'center',
        justifyContent: 'center',
        backgroundColor: '#ffffff',
    },
    input: {
        width: '80%',
        marginBottom: 10,
        padding: 10,
        borderWidth: 1,
        borderColor: '#cccccc',
        borderRadius: 5,
    },
    title: {
        fontSize: 18,
        fontWeight: 'bold',
        marginTop: 20,
    },
    name: {
        fontSize: 16,
        marginTop: 5,
    },
});
