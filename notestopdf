#!/usr/bin/python3

'''
Converts files from the notetaking program I use to pdfs for sharing.
'''


import os, sys
import cairosvg
import img2pdf
from PIL import Image

def svgzToPDF():
    dir = os.getcwd()

    svgzFname = sys.argv[1]
    svgzPath = os.path.join(dir, svgzFname)

    fnameNoType = svgzFname.split('.')[0]
    pngPath = os.path.join(dir, f'{fnameNoType}.png')

    cairosvg.svg2png(url=svgzPath, write_to=pngPath)
    print(f'Converted {svgzPath} to {pngPath}')

    image = Image.open(pngPath)
    pdfBytes = img2pdf.convert(image.filename)

    pdfPath = os.path.join(dir, f'{fnameNoType}.pdf')
    file = open(pdfPath, 'wb+')
    file.write(pdfBytes)

    image.close()
    file.close()

    print(f'Converted {pngPath} to {pdfPath}')
    os.remove(pngPath)
    print(f'Removed {pngPath}')

svgzToPDF()
