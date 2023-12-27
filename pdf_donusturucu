import streamlit as st
from pdf2docx import Converter
from io import BytesIO



st.title('PDF\'den DOCX\'e Dönüştürücü')

# Kullanıcıdan bir PDF dosyası yüklemesini isteyin
uploaded_file = st.file_uploader("PDF dosyası yükleyin", type=['pdf'])

if uploaded_file is not None:
    # Yüklenen PDF dosyasını okuyun ve bir BytesIO nesnesine dönüştürün
    bytes_data = uploaded_file.read()
    pdf_bytes_io = BytesIO(bytes_data)
    pdf_bytes_io.seek(0)

    # Dönüştürme işlemi için bir DOCX dosyası yolu belirleyin
    docx_bytes_io = BytesIO()

    # Dönüştürücüyü başlatın ve dönüştürme işlemini gerçekleştirin
    converter = Converter(pdf_bytes_io)
    converter.convert(docx_bytes_io)
    converter.close()

    # Dönüştürülen DOCX dosyasını indirme butonu ile kullanıcıya sunun
    docx_bytes_io.seek(0)
    st.download_button(
        label="Dönüştürülmüş DOCX'i İndir",
        data=docx_bytes_io,
        file_name='converted.docx',
        mime='application/vnd.openxmlformats-officedocument.wordprocessingml.document'
    )
