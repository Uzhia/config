# vimrc

```vim
" 启用语法高亮
syntax on

" 显示行号
set number

" 显示相对行号（方便跳转）
set relativenumber

" 高亮当前行
set cursorline

" 自动缩进
set autoindent
set smartindent

" 制表符设置（推荐用空格代替制表符）
set tabstop=4       " 一个Tab显示为4个空格
set shiftwidth=4    " 自动缩进时使用4个空格
set expandtab       " 将Tab转换为空格

" 启用鼠标支持（可选）
set mouse=a

" 搜索时忽略大小写，除非包含大写字母
set ignorecase
set smartcase

" 实时搜索高亮
set incsearch
set hlsearch

" 取消搜索高亮快捷键
nnoremap <silent> <Esc><Esc> :nohlsearch<CR>

" 启用文件类型检测并加载对应的插件和缩进规则
filetype plugin indent on

" 自动重新加载外部修改的文件
set autoread

" 禁止生成临时文件
set nobackup
set noswapfile

" 设置编码为UTF-8
set encoding=utf-8
set fileencoding=utf-8

" 允许隐藏缓冲区（避免未保存时切换文件报错）
set hidden

" 状态栏设置
set laststatus=2        " 总是显示状态栏
set statusline=%F\ %m%r%h%w\ [%Y]\ [%{&ff}]\ %=%l:%c\ %p%%

" 折叠设置（可选）
set foldmethod=indent   " 按缩进折叠
set foldlevel=99        " 默认不折叠
```
