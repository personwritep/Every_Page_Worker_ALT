// ==UserScript==
// @name        Every Page Worker 💢💢 ALT
// @namespace        http://tampermonkey.net/
// @version        5.5
// @description        「記事の編集・削除」でブログ全記事を開いて更新を実行
// @author        Ameba Blog User
// @match        https://blog.ameba.jp/ucs/entry/srventrylist*
// @match        https://blog.ameba.jp/ucs/entry/srventryupdate*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=ameba.jp
// @run-at        document-start
// @grant        none
// @updateURL        https://github.com/personwritep/Every_Page_Worker_ALT/raw/main/Every_Page_Worker_ALT.user.js
// @downloadURL        https://github.com/personwritep/Every_Page_Worker_ALT/raw/main/Every_Page_Worker_ALT.user.js
// ==/UserScript==



window.addEventListener('DOMContentLoaded', function(){ // CSSデザインを適用する
    let body_id=document.body.getAttribute('id');
    if(body_id=='entryListEdit'){ //「記事の編集・削除」の画面にのみCSS適用

        let box=
            '<div id="div_out">'+
            '<input id="list_snap" type="button" value="処理を再開　▶">'+
            'Card：<button id="card_thum" type="button" ></button>'+
            '<span id="snap_result">記録件数：</span>'+
            '<div id="div_in">'+
            '<span">Check🔵：</span>'+
            '<input id="num" type="number" min="0" max="1">'+
            '<input id="editor_open" type="button" value="編集">'+
            '</div>'+
            '<input id="reset" type="button" value="初期化">'+
            '<input id="export" type="button" value="Export">'+
            '<input id="import" type="button" value="Import">'+
            '<input id="import_in" type="file">'+
            '<button id="epwa_help">？</button>'+
            '</div>'+
            '<style>'+
            '#globalHeader, #ucsHeader, #ucsMainLeft h1, .l-ucs-sidemenu-area, .selection-bar { '+
            'display: none !important; } '+

            '#ucsContent { width: 930px !important; } '+
            '#ucsContent::before { display: none; } '+
            '#ucsMainLeft { width: 930px !important; padding: 0 15px !important; } '+

            '#entrySort { margin-bottom: 2px; } '+
            '#nowMonth { color: #000; } '+
            '#entryListEdit form { display: flex; flex-direction: column; } '+
            '#entrySort { order: -2; } '+
            '.pagingArea { order: -1; margin-bottom: -33px; position:unset !important; } '+
            '.pagingArea a { border: 1px solid #888; } '+
            '.pagingArea .active{ border: 2px solid #0066cc; } '+
            '.pagingArea a, .pagingArea .active, .pagingArea .disabled { font-size: 14px; line-height: 23px; } '+
            '#sorting { margin: 36px 0 4px; padding: 2px 0; height: 41px; position: relative; '+
            'background: #c0dbed !important; } '+
            '#sorting select, #sorting ul { display: none; } '+

            '#entryList .status-text { right: 374px !important; } '+
            '#entryList .entry-info .date { right: 260px !important; } '+
            '#entryList .actions { width: 240px; } '+

            '#div_out { font: 14px Meiryo; color: #000; ; margin: 0 -10px 0 15px; } '+
            '#list_snap { padding: 2px 0 0; margin: 7px 30px 7px 0; width: 140px; } '+
            '#card_thum { font: 14px Meiryo; height: 26.5px; width: 44px; padding: 2px 0 0; '+
            'border: 1px solid #777; border-radius: 2px; background: #fff; '+
            'position: absolute; top: 9px; left: 230px; } '+
            '#snap_result { display: inline-block; margin: 0 0 0 65px; } '+
            '#div_in { color: #000; font-size: 14px; position: absolute; top: 9px; left: 400px; } '+
            '#num { padding: 2px 2px 0 6px; width: 40px; } '+
            '#editor_open { padding: 2px 0 0; margin: 0 0 0 4px; width: 50px; } '+
            '#reset { padding: 2px 0 0; width: 60px; position: absolute; top: 9px; right: 210px; } '+
            '#export { padding: 2px 0 0; width: 66px; position: absolute; top: 9px; right: 120px; } '+
            '#import { padding: 2px 0 0; width: 68px; position: absolute; top: 9px; right: 40px; } '+
            '#import_in { display: none; } '+

            '#epwa_help { font: bold 19px/20px Meiryo; text-indent: -5px; height: 22px; '+
            'width: 22px; border: 1px solid #666; border-radius: 40px; background: #ffffff50; '+
            'position: absolute; top: 13px; right: 8px; cursor: pointer; } '+

            'input { font-family: meiryo; font-size: 14px; } '+
            '.ch1 { font: 15px/27px Meiryo; color: #0277bd; opacity: 0; margin-left: 8px; } '+
            '</style>';

        let sorting=document.querySelector('#sorting');
        if(sorting){
            if(!sorting.querySelector('#div_out')){
                sorting.insertAdjacentHTML('beforeend', box); }}

        let help_sw=document.querySelector('#epwa_help');
        if(help_sw){
            help_sw.onclick=(e)=>{
                e.preventDefault();
                let help_url="https://ameblo.jp/personwritep/entry-12935672810.html";
                window.open(help_url, '_blank', 'noopener=yes,noreferrer=yes'); }}

        let actions=document.querySelectorAll('#entryList .actions');
        for(let k=0; k<actions.length; k++){
            let iAH='<span class="ch1">🔵</span>';
            actions[k].insertAdjacentHTML('beforeend', iAH); }

    }})



window.addEventListener('load', function(){ // 親ウインドウで働くメインスクリプト
    let body_id=document.body.getAttribute('id');
    if(body_id=='entryListEdit'){ // 親ウインドウの条件

        let drive_mode; // ページ更新時の動作モード
        let card_img; // リンクカードのサムネイル仕様
        let blogDB={}; //「対象記事のID/チェックフラグ または内容」の記録配列

        let entry_id_DB; // ID検索用の配列
        let pub; // flag 1 が記録された記事総数

        let entry_id;
        let entry_target;
        let list_bar;
        let editor_flg;

        let next_target; // ページ内の次の対象記事
        let new_win;
        let link_target;
        let editor_iframe;
        let iframe_doc;


        let read_json=localStorage.getItem('EPWA_DB_back'); // ローカルストレージ 保存名
        blogDB=JSON.parse(read_json);
        if(blogDB==null){
            blogDB=[['epwa0000000', 's', 0]]; }
        drive_mode=blogDB[0][1]; // 起動時に動作フラグを取得
        card_img=blogDB[0][2]; // 起動時にカードサムネイル仕様を取得
        blogDB[0][1]='s'; // リロード時のためにリセット
        let write_json=JSON.stringify(blogDB);
        localStorage.setItem('EPWA_DB_back', write_json); // ローカルストレージ 保存

        reg_set();

        function reg_set(){
            let k;
            entry_id_DB=[]; // リセット
            pub=0;

            for(k=0; k<blogDB.length; k++){
                entry_id_DB[k]=blogDB[k][0]; // ID検索用の配列を作成
                if(blogDB[k][1]==1){
                    pub +=1; }}} // flag 1 が記録された記事総数（検索1）


        entry_id=document.querySelectorAll('input[name="entry_id"]');
        entry_target=document.querySelectorAll('.entry-item .entry');
        list_bar=document.querySelectorAll('#entryList .entry-item');


        control_pannel(drive_mode);

        hit_display();

        function control_pannel(dm){
            let button1=document.querySelector('#list_snap');

            if(dm=='s'){
                button1.value='処理を開始　▶'; }
            else if(dm=='c'){
                button1.value='一旦停止　　❚❚'; }
            else if(dm=='e'){
                button1.value='処理が全て終了'; }


            button1.addEventListener('click', function(e){
                e.preventDefault();
                if(e.ctrlKey){
                    start_stop(1); } // ページの途中から連続処理スタート
                else if(e.shiftKey){
                    start_stop(2); } // ページの途中の1記事のみ処理
                else{
                    start_stop(0); }}, false);


            function start_stop(n){
                if(drive_mode=='s'){ // 最初の起動直後
                    if(n==0){
                        let conf_str='　 🔴　このページの先頭から連続した処理を開始します'+
                            '\n\n　　　  停止ボタンのクリックで処理停止/処理再開ができます\n';
                        let ok=confirm(conf_str);
                        if(ok){
                            drive_mode='c'; // ページ内の連続処理
                            button1.value='一旦停止　　❚❚';
                            next(0); }}
                    else if(n==1){
                        alert('　🔴　左クリックした記事から連続した処理を開始します');
                        drive_mode='c'; // ページ内の連続処理
                        button1.value='一旦停止　　❚❚';
                        clicked_item(); }
                    else if(n==2){
                        drive_mode='m'; // ページ内の単一処理
                        button1.value='❚❚❚❚ 単一処理 ❚❚❚❚';
                        clicked_item(); }}

                else if(drive_mode=='c'){ // 連続動作状態の場合
                    drive_mode='p'; // クリックされたら「p」停止モード
                    button1.value='処理を再開　　▶'; }

                else if(drive_mode=='p'){ // 動作停止状態の場合
                    drive_mode='c'; // クリックされたら連続動作を再開
                    button1.value='一旦停止　　❚❚';
                    open_win(next_target); }

                function clicked_item(){
                    let entry_item=document.querySelectorAll('.entry-item');
                    for(let k=0; k<entry_item.length; k++){
                        entry_item[k].onclick=function(e){
                            e.preventDefault();
                            e.stopImmediatePropagation();
                            next(k); }}}
            } // start_stop()


            if(dm=='c'){ // ページを開いた時に「c」は連続動作
                setTimeout(next(0), 200); } //「c」連続動作はぺージ遷移時 0.2sec で自動実行 ⭕
            else if(dm=='e'){ //「e」は終了
                button1.style.pointerEvents='none'; }

            card_img_set();
            snap_disp();
            pub_edit();
            reset_data();
            backup();

        } // control_pannel()



        function card_img_set(){
            let card_thum=document.querySelector('#card_thum');
            if(card_img==0){
                card_thum.textContent='🔗';
                card_thum.style.background='#fff'; }
            else{
                card_thum.textContent='Text';
                card_thum.style.background='#00f1f1'; }

            card_thum.onclick=()=>{
                if(card_img==0){
                    card_img=1;
                    card_thum.textContent='Text';
                    card_thum.style.background='#00f1f1';
                    blogDB[0][2]=1; }
                else{
                    card_img=0;
                    card_thum.textContent='🔗';
                    card_thum.style.background='#fff';
                    blogDB[0][2]=0; }

                let write_json=JSON.stringify(blogDB);
                localStorage.setItem('EPWA_DB_back', write_json); } // ローカルストレージ 保存

        } // card_img_set()



        function snap_disp(){
            reg_set();
            let snap_r=document.querySelector('#snap_result');
            snap_r.textContent='記録件数：' + (blogDB.length -1);
            let button6=document.querySelector('#num');
            button6.value=pub;
            button6.max=pub; }



        function pub_edit(){
            let button6=document.querySelector('#num');
            let button7=document.querySelector('#editor_open');
            button7.onclick=function(e){
                e.preventDefault();
                let k;
                let pub_DB=[]; // pub の entry_id の配列
                if(pub>0){
                    for(k=0; k<blogDB.length; k++){
                        if(blogDB[k][1]==1){
                            pub_DB.push(blogDB[k][0]); }}

                    if(button6.value>0){
                        let open_id=pub_DB[button6.value -1];
                        let pass=
                            'https://blog.ameba.jp/ucs/entry/srventryupdateinput.do?id='+ open_id;
                        let win_option='top=20, left=40, width=1020, height=900';
                        window.open(pass, button6.value, win_option); }}}

        } // pub_edit()



        function reset_data(){
            let button2=document.querySelector('#reset');
            button2.onclick=function(e){
                e.preventDefault();
                let conf_str=
                    '　 🔴　これまでの処理で保存された記事のデータを全て削除します\n'+
                    '　　　  データを削除して良い場合は「OK」を押します\n'+
                    '　  ▶　「キャンセル」してファイル保存をすると、後でデータを戻せます\n';
                let ok=confirm(conf_str);
                if(ok){
                    blogDB=[['epwa0000000', 's', 0]];
                    let write_json=JSON.stringify(blogDB);
                    localStorage.setItem('EPWA_DB_back', write_json); // ローカルストレージ保存
                    snap_disp();
                    hit_display_clear();
                    document.querySelector('#reset').value='〔　〕'; }}

        } // reset_data()



        function backup(){
            let button3=document.querySelector('#export');
            button3.onclick=function(e){
                e.preventDefault();
                let write_json=JSON.stringify(blogDB);
                let blob=new Blob([write_json], {type: 'application/json'});
                let a_elem=document.createElement('a');
                a_elem.href=URL.createObjectURL(blob);
                a_elem.download='EPWA.json'; // 保存ファイル名
                a_elem.click();
                URL.revokeObjectURL(a_elem.href); }


            let button2=document.querySelector('#reset');
            let button4=document.querySelector('#import');
            let button5=document.querySelector('#import_in');
            button4.onclick=()=>{ button5.click(); }

            button5.addEventListener("change", function(){
                if(!(button5.value)) return; // ファイルが選択されない場合
                let file_list=button5.files;
                if(!file_list) return; // ファイルリストが選択されない場合
                let file=file_list[0];
                if(!file) return; // ファイルが無い場合

                let file_reader=new FileReader();
                file_reader.readAsText(file);
                file_reader.onload=function(){
                    if(file_reader.result.slice(0, 15)=='[["epwa0000000"'){ // EPWA.jsonの確認
                        let data_in=JSON.parse(file_reader.result);
                        blogDB=data_in; // 読込み上書き処理
                        let write_json=JSON.stringify(blogDB);
                        localStorage.setItem('EPWA_DB_back', write_json); // ローカルストレージ 保存
                        button2.value='初期化'; // 初期化後なら読み込んだ事を示す
                        snap_disp();
                        hit_display(); }
                    else{
                        alert("　⛔ 不適合なファイルです  EPWA.json ファイルを選択してください");}};

                setTimeout(()=>{
                    this.value=null; // 同ファイルの再読込みを可能にする
                }, 1000);
            });

        } // backup()



        function hit_display(){
            let ch1=document.querySelectorAll('.ch1');
            for(let k=0; k<ch1.length; k++){
                let index=entry_id_DB.indexOf(entry_id[k].value);
                if(index!=-1){ // IDがblogDBに記録されていた場合
                    if(blogDB[index][1]==1){
                        ch1[k].style.opacity='1'; }
                    else{
                        ch1[k].style.opacity='0'; }}
                else{
                    ch1[k].style.opacity='0'; }}}


        function hit_display_clear(){
            let ch1=document.querySelectorAll('.ch1');
            for(let k=0; k<ch1.length; k++){
                ch1[k].style.opacity='0'; }}



        function next(x){ // xはページ内の記事index[0～length-1]
            entry_id=document.querySelectorAll('input[name="entry_id"]');
            if(entry_id.length >x){
                open_win(x); } // 投稿記事がある場合 open_win を開始
            else{
                next_call();}} // 投稿記事が無ければ 次ページをcall する



        function open_win(k){
            next_target=k; // 送信完了までは未処理とする

            new_win=Array(entry_target.length);
            link_target=Array(entry_target.length);
            link_target[k]='/ucs/entry/srventryupdateinput.do?id='+ entry_id[k].value;

            if(drive_mode=='c' || drive_mode=='m'){
                let win_option='top=60, left=0, width=800, height=300';
                new_win[k]=window.open(link_target[k], k, win_option);

                list_bar[k].style.boxShadow='inset 0 0 0 2px #03a9f4'; // リスト欄に青枠表示
                new_win[k].addEventListener('load', work, false); } // 子ウインドウの処理 🟦


            function work(){
                let editor_flg=new_win[k].document.querySelector('input[name="editor_flg"]');
                if(editor_flg.value=="5"){ // 最新版エディタの文書の場合のみ処理

                    let interval=setInterval(find_iframe, 100); // iframe 読込み待機コード ⬛ Speed調節 ⬛
                    function find_iframe(){
                        let editor_iframe=new_win[k].document.querySelector('.cke_wysiwyg_frame');
                        if(editor_iframe){
                            let iframe_doc=editor_iframe.contentWindow.document;
                            if(iframe_doc){
                                clearInterval(interval);
                                task();


                                function task(){ // taskは自動で開いたページでの作業コード 🟥
                                    let promise=new Promise((resolve, reject)=>{
                                        setTimeout(()=>{
                                            let all_img=iframe_doc.querySelectorAll('img');
                                            if(all_img.length==0){ // 編集非対応 🟥🟧🟥
                                                send_result(0); // 処理結果をデータ保存
                                                reject(); }
                                            else{ // リンクカードのALT書換え＋画像のALTのチェック🟥🟧🟥
                                                let check=0;
                                                for(let k=0; k<all_img.length; k++){
                                                    if(all_img[k].classList.contains('ogpCard_image')){
                                                        if(card_img==0){
                                                            all_img[k].setAttribute('alt', '🔗'); }
                                                        if(card_img==1){
                                                            all_img[k].setAttribute('alt', ''); }}
                                                    else{
                                                        if(all_img[k].getAttribute('alt')=='' ||
                                                           all_img[k].getAttribute('alt')==null){
                                                            let ogp=all_img[k].closest('.ogpCard_root');
                                                            let pick=all_img[k].closest('.pickCreative_root');
                                                            if(!ogp && !pick){ // リンク・ピックカード以外はALT必要
                                                                check+=1; }}}}

                                                resolve(check); }
                                        },400);

                                    })
                                    .then((check)=>{
                                        if(check==0){ // ALTの正常適用 🟥🟧🟥
                                            send_result(0); } // 処理結果をデータ保存
                                        else{ // ALT適用がされない記事 🟥🟧🟥
                                            send_result(1); } // 処理結果をデータ保存

                                        publish_do(k); // 編集結果を投稿 🟥🟧🟥

                                    })
                                    .catch(()=>{
                                        ;

                                    })
                                    .then((not)=>{
                                        strage_write();
                                        snap_disp();
                                        hit_display();
                                        end_target(); // 再編集のウインドウを閉じる

                                    });
                                } // task()


                                function send_result(n){
                                    let index=entry_id_DB.indexOf(entry_id[k].value);
                                    if(index==-1){ // IDがblogDBに記録されていない場合
                                        if(n==1){
                                            blogDB.push([entry_id[k].value, 1, 0]); }} // 記事ID/フラグを追加
                                    else{ // IDがblogDBに記録されていた場合
                                        if(n==1){
                                            blogDB[index][1]=1; } // 記事ID/フラグ「1」を更新
                                        else{
                                            blogDB.splice(index, 1); }} // 記事IDの登録を削除
                                    reg_set(); }


                                function strage_write(){
                                    let write_json=JSON.stringify(blogDB);
                                    localStorage.setItem('EPWA_DB_back', write_json); }// ストレージ保存


                                function publish_do(k){
                                    let publish_flg=new_win[k].document.querySelector('input[name="publish_flg"]');
                                    let val=publish_flg.getAttribute('value');

                                    let publish_b0=new_win[k].document.querySelector('button.js-submitButton[publishflg="0"]');
                                    let publish_b1=new_win[k].document.querySelector('button.js-submitButton[publishflg="1"]');
                                    if(val=='0'){ publish_b0.click(); }
                                    if(val=='1'){ publish_b1.click(); }
                                    if(val=='2'){ publish_b0.click(); }}

                            }}}

                } // if(editor_flg.value=="5") // 最新版エディタの文書の場合のみ処理

                else{ // タグ編集エディタの場合
                    let index=entry_id_DB.indexOf(entry_id[k].value);
                    if(index==-1){ // IDがblogDBに記録されていない場合
                        blogDB.push([entry_id[k].value, 1, 0]); } // 記事ID/フラグを追加
                    else{ // IDがblogDBに記録されていた場合
                        blogDB[index][1]=1; } // 記事ID/フラグ「1」を更新
                    reg_set();

                    end_target(); }

            } // work()


            function end_target(){ // 終了処理
                let editor_flg=new_win[k].document.querySelector('input[name="editor_flg"]');
                list_bar[k].style.boxShadow='none';
                if(editor_flg.value=='5'){
                    list_bar[k].style.background='#caedf2'; }
                else{
                    list_bar[k].style.background='#eceff1'; }

                new_win[k].close();
                setTimeout(()=>{
                    if(drive_mode=='c'){ // 連続処理
                        next_do(k); }
                    if(drive_mode=='m'){ // 単一のファイル処理
                        location.reload(); }}, 10); //⏩

                function next_do(k){
                    next_target=k+1;
                    if(next_target<entry_target.length){ open_win(next_target); }
                    else{ next_call(); }}} // ページの終りまで終了した状態

        } // open_win()



        function next_call(){
            let win_url;
            let current;
            let pageid;
            let next_url;
            let pager;
            let end;

            blogDB[0][1]='c'; // 連続動作フラグを連続にセット
            let write_json=JSON.stringify(blogDB);
            localStorage.setItem('EPWA_DB_back', write_json); // ローカルストレージ保存

            win_url=window.location.search.substring(1,window.location.search.length);
            current=win_url.slice(-6);

            if(win_url.indexOf('pageID') ==-1){ // pageIDが無い 月のトップページの場合
                pager=document.querySelector('.pagingArea');
                if(pager){ // ページャーが有りその末尾でなければ同月次ページへ
                    next_url=
                        'https://blog.ameba.jp/ucs/entry/srventrylist.do?pageID=2&entry_ym=' + current;
                    window.open( next_url, '_self'); }
                else{ // ページャーが無ければ次月トップページへ
                    current=make_next(current);
                    if(current!=0){ // 現在を越えないなら次月へ
                        next_url=
                            'https://blog.ameba.jp/ucs/entry/srventrylist.do?entry_ym=' + current;
                        window.open( next_url, '_self'); }
                    else{ // 現在を越えたら0が戻り停止
                        when_edge(); }}}

            else{ // pageIDを含み 月のトップページでない場合
                end=document.querySelector('.pagingArea .disabled.next');
                if(!end){ // ページャーの末尾でなければ同月次ページへ
                    pageid=parseInt(win_url.slice(7).slice(0, -16), 10) +1;
                    next_url=
                        'https://blog.ameba.jp/ucs/entry/srventrylist.do?pageID='+ pageid + '&entry_ym=' + current;
                    window.open( next_url, '_self'); }
                else{ // ページャーの末尾なら次月トップページへ
                    current=make_next(current);
                    if(current!=0){ // 現在を越えないなら次月へ
                        next_url=
                            'https://blog.ameba.jp/ucs/entry/srventrylist.do?entry_ym=' + current;
                        window.open( next_url, '_self'); }
                    else{ // 現在を越えたら0が戻り停止
                        when_edge(); }}}

            function make_next(curr){
                let ym;
                let y;
                let m;
                ym=parseInt(curr, 10); // 10進数値化
                y=Math.floor(ym/100); // 年は100で割った商
                m=ym % 100; // 月は100で割った余り
                if(m !=12){
                    ym=100*y + m +1; }
                else{
                    ym=100*y + 101; }

                let now=new Date();
                if(ym > 100*now.getFullYear() + now.getMonth() +1){
                    return 0; } // 現在の月を越える場合は0を返す
                else{
                    return ym; }} // 次年月の数値を返す

            function when_edge(){
                blogDB[0][1]='s'; // 連続動作フラグをリセット
                let write_json=JSON.stringify(blogDB);
                localStorage.setItem('EPWA_DB_back', write_json); // ローカルストレージ保存
                control_pannel('e'); } // 全作業の終了時の表示をさせる
        } // next_call()


        // 編集済みの記事にマークを付ける
        let ed_sw=document.querySelectorAll('.actions .action:first-child');
        for(let k=0; k<ed_sw.length; k++){
            ed_sw[k].onmousedown=()=>{
                ed_sw[k].style.boxShadow='inset #2196f3 -16px 0 0 -10px'; }}

        let ed_link=document.querySelectorAll('.actions a');
        for(let k=0; k<ed_link.length; k++){
            ed_link[k].setAttribute('target', '_blank'); }

    } // 親ウインドウの条件




    if(body_id=='entryCreate'){ // 投稿後の終了画面
        let err=document.querySelector('.p-error');
        if(!err){
            window.close();
        }}
});
