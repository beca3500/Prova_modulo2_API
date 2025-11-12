from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/gols')
def gols():
    jogador = request.args.get('jogador')
    gols = request.args.get('gols')

    # Verifica se os parâmetros foram enviados
    if not jogador or not gols:
        return jsonify({"erro": "Parâmetros 'jogador' e 'gols' são obrigatórios!"}), 400

    # Verifica se gols é um número
    try:
        gols = int(gols)
    except ValueError:
        return jsonify({"erro": "O parâmetro 'gols' deve ser um número inteiro!"}), 400

    mensagem = f"O jogador {jogador} marcou {gols} gols!"
    return jsonify({"mensagem": mensagem})

if __name__ == '__main__':
    app.run(debug=True)



