{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyPUn4hqtvo9LDZ8P/Jr7KIR",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/192465036simats-hash/CSA6102-Digital-forensics-and-cybercrime-investigation/blob/main/Lab%20/EXP24/README.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "XIgW1jGZ6sr3",
        "outputId": "dd5bf9df-8162-4c8a-ec12-ead543b10084"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "hello -> {'MD5': '5d41402abc4b2a76b9719d911017c592', 'SHA1': 'aaf4c61ddcc5e8a2dabede0f3b482cd9aea9434d', 'SHA256': '2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824'}\n",
            "Hello -> {'MD5': '8b1a9953c4611296a827abf8c47804d7', 'SHA1': 'f7ff9e8b7bb2e09b70935a5d785e0cc5d9d0abf0', 'SHA256': '185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969'}\n",
            "Experiment 7: All test cases passed.\n"
          ]
        }
      ],
      "source": [
        "import hashlib\n",
        "\n",
        "def compute_hashes(data: bytes):\n",
        "    return {\n",
        "        \"MD5\": hashlib.md5(data).hexdigest(),\n",
        "        \"SHA1\": hashlib.sha1(data).hexdigest(),\n",
        "        \"SHA256\": hashlib.sha256(data).hexdigest()\n",
        "    }\n",
        "\n",
        "original_data = b\"hello\"\n",
        "tampered_data = b\"Hello\"\n",
        "\n",
        "hashes_original = compute_hashes(original_data)\n",
        "hashes_tampered = compute_hashes(tampered_data)\n",
        "hashes_original_repeat = compute_hashes(original_data)\n",
        "\n",
        "print(\"hello ->\", hashes_original)\n",
        "print(\"Hello ->\", hashes_tampered)\n",
        "\n",
        "def test_experiment7():\n",
        "    assert hashes_original == hashes_original_repeat\n",
        "    assert hashes_original[\"MD5\"] != hashes_tampered[\"MD5\"]\n",
        "    assert hashes_original[\"SHA256\"] != hashes_tampered[\"SHA256\"]\n",
        "    print(\"Experiment 7: All test cases passed.\")\n",
        "\n",
        "test_experiment7()"
      ]
    }
  ]
}