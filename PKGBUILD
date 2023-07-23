pkgname=llama2-chat

_llamaversion=master-d2a4366
pkgver=1.0.1
pkgrel=1
pkgdesc="Llama2 chat using the uncensored Luna AI ggml quantized version"
arch=('aarch64' 'x86_64')
license=('custom:LLAMA 2 COMMUNITY LICENSE AGREEMENT')
makedepends=(git)
source=(git+https://github.com/ggerganov/llama.cpp.git#tag=$_llamaversion
        https://huggingface.co/TheBloke/Luna-AI-Llama2-Uncensored-GGML/resolve/main/luna-ai-llama2-uncensored.ggmlv3.q3_K_S.bin
        llama2-chat
        luna_ai_prompt.txt
        LICENSE
)
sha256sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
)

build() {
    cd llama.cpp
    make
}

package() {
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

    install -Dm755 llama.cpp/main "$pkgdir/usr/bin/llama2"
    install -Dm755 llama2-chat "$pkgdir/usr/bin/llama2-chat"


    install -Dm0755 luna-ai-llama2-uncensored.ggmlv3.q3_K_S.bin "${pkgdir}/opt/llama2/models/7B/luna-ai-llama2-uncensored.ggmlv3.q3_K_S.bin"
    install -Dm0755 luna_ai_prompt.txt "${pkgdir}/opt/llama2/prompts/7B/luna_ai_prompt.txt"
}
