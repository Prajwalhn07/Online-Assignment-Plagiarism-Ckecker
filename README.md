# Online-Assignment-Plagiarism-Ckecker# 
app.py - Flask backend
from flask import Flask, request, jsonify, render_template
import difflib
import re

app = Flask(__name__)

def preprocess_text(text):
    """Clean and tokenize text."""
    # Remove punctuation and lowercase
    text = re.sub(r'[^\w\s]', '', text).lower()
    return set(text.split())

@app.route('/')
def home():
    return render_template('index.html')

@app.route('/check', methods=['POST'])
def check_plagiarism():
    # Assume we get two text inputs from the form
    text1 = request.form.get('text1')
    text2 = request.form.get('text2')

    if not text1 or not text2:
        return jsonify({'error': 'Please provide both texts.'}), 400

    # Preprocess the texts
    set1 = preprocess_text(text1)
    set2 = preprocess_text(text2)

    # Jaccard Similarity Calculation
    intersection = set1.intersection(set2)
    union = set1.union(set2)
    jaccard_similarity = len(intersection) / len(union) if union else 0

    # Find matching lines using difflib for highlighting
    s = difflib.SequenceMatcher(None, text1.splitlines(), text2.splitlines())
    matches = s.get_matching_blocks()

    # Create a list of matching spans for the frontend to highlight
    match_details = []
    for block in matches:
        if block.size > 0:
            match_details.append({
                'text1_start': block.a,
                'text1_end': block.a + block.size,
                'text2_start': block.b,
                'text2_end': block.b + block.size
            })

    return jsonify({
        'plagiarism_score': f'{jaccard_similarity * 100:.2f}%',
        'match_details': match_details
    })

if __name__ == '__main__':
    app.run(debug=True)
