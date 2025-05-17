GVIM版本的vimrc

```vim
" === 基础设置 ===
set nocompatible        " 禁用 Vi 兼容模式
syntax on               " 语法高亮
filetype plugin indent on " 启用文件类型检测

" === 显示优化 ===
set number              " 显示行号
set relativenumber      " 显示相对行号（方便跳转）
set cursorline          " 高亮当前行
set scrolloff=5         " 光标距离顶部/底部保留5行
set nowrap              " 不自动换行（如需换行可改为 `set wrap`）

" === 缩进与制表符 ===
set tabstop=4           " Tab显示为4个空格
set shiftwidth=4        " 自动缩进时使用4个空格
set expandtab           " 将Tab转换为空格
set smartindent         " 智能缩进

" === 搜索与替换 ===
set ignorecase          " 搜索忽略大小写
set smartcase           " 如果包含大写则区分大小写
set hlsearch            " 高亮搜索结果
set incsearch           " 实时搜索高亮
nnoremap <silent> <Esc><Esc> :nohlsearch<CR> " 按两次Esc取消高亮

" === 文件编码 ===
set encoding=utf-8      " 内部编码
set fileencoding=utf-8  " 文件保存编码

" === 剪贴板集成 ===
set clipboard=unnamedplus " 直接使用系统剪贴板（需GVim支持）

" === 禁用临时文件 ===
set nobackup
set noswapfile

" === 状态栏增强 ===
set laststatus=2        " 总是显示状态栏
set statusline=%F\ %m%r%h%w\ [%Y]\ [%{&ff}]\ %=%l:%c\ %p%%

" === GVim 专属设置 ===
if has('gui_running')
    " 隐藏菜单栏和工具栏
    set guioptions-=m
    set guioptions-=T
    set guioptions-=r  " 隐藏右侧滚动条
    set guioptions-=L  " 隐藏左侧滚动条

    " 设置字体（根据系统调整）
    if has('win32')
        set guifont=Consolas:h12
    elseif has('mac')
        set guifont=Menlo\ Regular:h14
    else
        set guifont=DejaVu\ Sans\ Mono\ 11
    endif

    " 初始窗口大小
    set lines=40 columns=120

    colorscheme desert
    set background=dark   " 深色模式
endif

" === 快捷键映射 ===
" 窗口切换
nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

" 启用鼠标支持（可选）
set mouse=a
" 自动重新加载外部修改的文件
set autoread
" 允许隐藏缓冲区（避免未保存时切换文件报错）
set hidden
set foldmethod=indent   " 按缩进折叠
set foldlevel=99        " 默认不折叠


" === 自动命令 ===
" 保存时去除行尾空格
autocmd BufWritePre * %s/\s\+$//e

```
