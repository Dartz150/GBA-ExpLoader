======  GBA ExpLoader V0.57  ======

Slot2タイプ拡張パックを利用して、Slot-1カードのGBAのゲームを起動します。

ソフトリセットが可能なSlot-1カードでは、「DS振動カートリッジ」と「DS拡張メモリ」
として利用する事ができます。

サポートしているSlot2タイプ拡張パックは、「3in1拡張パック」「EZ4 lite-delux」
と「EWIN EXPANSION PAK, DSTT GBA&EXPLORER 2IN1」です。
また、「M3」「G6」「GBA Expansion Pack」を暫定でサポートしています。
但し「NORモード」と「DS振動カートリッジ」は、「3in1拡張パック」のみのサポートになります。


＜3in1拡張パックの仕様＞
1. 256Mbit(32MByte) NORfalsh	page size is 1Mbits(128KB)
2. 128Mbit(16MByte) PSRAM	page size is 1Mbits(128KB)
3. 4Mbit(512KByte)  SRAM	page size is 64Kbits(8KB)

＜EZ FlashIV lite-deluxの仕様＞
1. 384Mbit(48MByte) NORfalsh	page size is 1Mbits(128KB)
2. 256Mbit(32MByte) PSRAM	page size is 1Mbits(128KB)
3. 8Mbit(1MByte)    SRAM	page size is 64Kbits(8KB)

＜EWIN EXPANSION PAKの仕様＞
1. 256Mbit(32MByte) SDRAM
2. 2Mbit(256KByte)  SRAM	page size is 256Kbits(64KB)

＜DSTT GBA&EXPLORER 2IN1の仕様＞
1. 256Mbit(32MByte) SDRAM
2. 1Mbit(128KByte)  SRAM	page size is 256Kbits(64KB)

＜GBA Expansion Packの仕様＞
1. 256Mbit(32MByte) SDRAM
2. 8Mbit(1MByte)    SRAM	page size is 256Kbits(64KB)


＜導入方法＞
「GBA_ExpLoader.NDS」は、DLDI対応ですので利用するSlot-1カードに合わせて
パッチしてください(通常は自動DLDIパッチなのでそのままで動作します)。

・SDのルートに、"/GBA_SAVE"と"/GBA_SIGN"フォルダを作成します
　(iniファイルにて、ディレクトリを指定した場合はそのディレクトリを作成します)。
・GBAファイルを入れます(場所は任意の位置でいいです)。
・"/GBA_SAVE"フォルダに、GBAファイルと同じ名前でSAVファイルを入れます
　(SAVファイルが無い場合は、新規でGBAファイルと同じ名前でSAVファイルが作成されます)。
・GBA起動時にフレームを使用したい場合は、gbaframe.bmp(24bitもしくは8bit)を
　ルート、SignDir、"/_system_"フォルダのいずれかに入れてください(記載順で検索)。


＜GBA ExpLoader.ini＞
各種動作環境の設定を記入します。'#'と'!'以降のその行の文字はコメントとして扱われます。
GBA ExpLoader.iniは、SDのルートディレクトリに必ず置いてください。
ロングファイル名のディレクトリを指定する場合は、"/GBA SAVE"のようにダブルコーテーションで
括ってください。
　・SaveDir
　　　SAVファイルを格納するSDのディレクトリを指定します(初期値は、/GBA_SAVE)。
　・SignDir	0
　　　SGNファイルとheader.datを格納するSDのディレクトリを指定します(初期値は、/GBA_SIGN)。
　・No_MultiSave
　　　複数のSAVファイルを選択して取り扱う事を止めます(指定しない事で、MultiSAVEになります)。


===《 重 要 》===========================================================================
3in1_ExpPack_Toolとは、SRAMの管理情報が異なっています。
3in1_ExpPack_Toolや他のツールと併用することはできません。
他のツールで使用していた拡張パックを利用する場合は、必ずSRAMのバックアップを
取ってから使用してください。
=========================================================================================


＜使用方法＞
・「GBA_ExpLoader.NDS」を起動します。
・「3in1拡張パック」では、<L><R>でPSRAMモード・NORモード・拡張モード(サポートされている場合のみ)を
　 切り替えます。

　自動的に、PSRAM/SDRAMモードで前回起動した時の保存されていないSRAMのSAVEデータを、SAVファイルに保存します。
　SAVファイルへの保存は、選択したSAVファイルに保存します(「保存しない」事も可能)。

　(PSRAM/SDRAMモード)
　・<A>：選択したGBAファイルをSRAMパッチ後にPSRAMに書込みます。
　　　　 また、そのGBAの選択したSAVファイルをSRAMにロードします。
　　　　 PSRAMからGBAを起動します。
　・<B>：現在のSRAMのSAVEを、選択したSAVファイルに保存します。

　・<Y>：<X>でバックアップした、SRAM.BINをSRAMに書き込みます。
　・<X>：全SRAM(512KB)を、SRAM.BINというファイルにバックアップします。

　・<R>：ブラウザ拡張メモリに、設定してソフトリセットします(「3in1拡張パック」以外)。


　　「3in1拡張パック」の場合は、PSRAMで実行できるファイルのサイズは16MByte(正確には16000KB)です。

　　画面には表示されていませんが、リセットがサポートされているカードでは<SELECT>で
　　<A>のGBA起動の代わりにメニューに戻ります。
　　DSの電源切入・拡張パックの抜き差しをするまではRAMからのGBA起動が可能です。

　　SAVファイルを取り替えたい場合等は、一度<B>で保存した(もしくは違うゲームを
　　PSRAMで起動)後に、SAVファイルを入れ替えることで反映します。
　　同一のゲームを続けて行う場合でも毎回選択したSAVファイルをSRAMに書込みます。


　(NORモード)「3in1拡張パック」のみ

　・<A>：現在のSRAMのSAVEを選択したSAVファイルに保存します。
	 選択したGBAファイルをSRAMパッチ後にNORにコピーします。
　　　　 また、そのGBAの選択したSAVファイルをSRAMにロードします。
　・<B>：現在のSRAMのSAVEを選択したSAVファイルに保存します。
　・<Y>：現在のNORのGBA用の選択したSAVファイルをSRAMにロードします。
　・<X>：NOR利用モードで、GBA(Slot-2)を起動します。

　　<X>のGBA(Slot-2)起動は、拡張パック単独での起動とまったく同じ動作です。


　(拡張モード)「3in1拡張パック」のみ
　 振動レベル(小・中・大)とブラウザ拡張メモリに、設定してソフトリセットします。


＜3in1拡張パックとEZ4でのSRAMの構成＞
　SRAMは、512KB(4Mbit)で8KB(64Kbits)単位のページングで使用できます。
　NORをGBAカートとして使う場合を考慮してNOR用のSAVEはオフセット64KBから使っています。
　　 64KB　　　　未使用
　　128KB　　　　NOR用SAVE
　　　8KB　　　　SAVE管理エリア
　　128KB　　　　PSRAM用SAVE
　　残り　　　　 未使用

＜EWIN EXPANSION PAKでのSRAMの構成＞
　SRAMは、256KB(1Mbit)で64KB(256Kbits)単位のページングで使用できます。
　　128KB　　　　SDRAM用SAVE
　　 64KB　　　　SAVE管理エリア
　　 64KB　　　　未使用

＜DSTT GBA&EXPLORER 2IN1でのSRAMの構成＞
　SRAMは、256KB(1Mbit)で64KB(256Kbits)単位のページングで使用できます。
　SAVE管理ファイルは、SignDirに"EXP128K.dat"のファイル名で作成されます。
　　128KB　　　　SDRAM用SAVE
　　1.5KB　　　　SAVE管理ファイル(EXP128K.dat)

＜GBA Expansion Pack(M3/G6)でのSRAMの構成＞
　SRAMは、256KB(1Mbit)で64KB(256Kbits)単位のページングで使用できます。
　　256KB　　　　未使用
　　128KB　　　　SDRAM用SAVE
　　 64KB　　　　SAVE管理エリア
　　残り 　　　　未使用


＜ソフトリセットについて＞
　ソフトリセットが可能なSlot-1カードは次のものです。
　①標準サポート(ダイレクト起動)
	R4/M3Simply
	DSLink
　②システムファイルを利用
	SCDS(ONE)
	N-Card		udisk.ndsをSDルートにコピー
	Acekard R.P.G	akmenu4.ndsをSDルートにコピー
	X9SD
	DSTT(TTDS)
　③ファームウェア等を利用
	カードのファームウェアをバックアップしたNDSファイル等を、SoftReset.DLDI名(4文字)と
	いう名前でSDルートに置くことによってリセットする。

　・EZ5では①のソフトリセットが可能ですが、カーネルメニューにて「3in1拡張パック」を初期設定しているため
　　「DS振動カートリッジ/DS拡張メモリ」としての設定が無効になってしまうためサポートしていません。


＜ヘッダの修復について＞
　ヘッダ情報が不正な、GBAファイルを自動的に修復して起動します(BINファイルは修復しません)。
　諸般の事情により、ヘッダ修復機能を利用したい場合は下記の手順でセットアップしてください。
　製品版のGBAファイルの先頭から256Byteを切り出し、header.datという名前で/GBA_SIGNフォルダに
　コピーします(切り出しが分からない方は、なるべく小さいGBAファイルをそのままheader.datとして
　コピーしてください)。


＜注意等＞
・SAVEタイプがSRAMタイプ以外の場合には、自動的にSRAMパッチを施します。
　SRAMパッチをサポートしているSAVEの形式は下記の通りです。
	EEPROM_V111、EEPROM_V120、EEPROM_V121、EEPROM_V122、EEPROM_V124、EEPROM_V125、EEPROM_V126
	FLASH_V120、FLASH_V121、FLASH_V123、FLASH_V124、FLASH_V125、FLASH_V126
	FLASH512_V130、FLASH512_V131、FLASH512_V133
	FLASH1M_V102、FLASH1M_V103
	Famicom Mini(Classic NES)の特殊なEEPROM_V122、EEPROM_V124、未定義タイプ
・SAVファイルのサイズは、実際のSAVEのサイズにしています。但し、EEPROMタイプでは
　512Bか8KBかの判別が不可能なため全て8KBとしています。
・SAVEタイプが判別不可能(SAVEなしも含む)な場合は、SAVEタイプをSRAMタイプと仮定して
　処理しています(SAVファイルのサイズは64KB)。
・実際のSAVファイルのサイズは、先頭からが有効なデータであれば大きくても構いません。
・SAVファイルは、GBAファイルと同じ名前でSaveDirフォルダに作成されます。
・2回目の起動からSRAMパッチを高速に行うために、アナライズしたパッチ情報を
　SignDirフォルダにSGNファイルとして作成します。
・拡張子をBINとしたファイルでは、パッチ処理を行いません。homebrewやパッチ済みの場合は、拡張子を
　GBAではなくBINとしてください。また、その場合のSAVファイルのサイズは64KBとなります。
・SAVEファイルの選択で、SAVは拡張子がsavとなります。<1>から<5>は、sv1からsv5になります。
・SAVファイルとSGNファイル用のフォルダは、できるだけ自分で作成してください
  (Slot-1カードの種類によっては正しく作成されません。N-Card系では時間が非常に長くかかります)。
　また、複数階層のディレクトリは自動では作成できませんので必ず自分で作成してください。
・暫定サポートの「M3」「G6」「GBA Expansion Pack」では、FLASH1Mタイプのパッチは行いません(未完成)。
・「DSTT GBA&EXPLORER 2IN1」では、SAVE管理をファイルで行っていますので複数の「DSTT GBA&EXPLORER 2IN1」を
　使い分けることはできません。また、Slot-1側のSDも使い分けできませんので注意が必要です。

＜履歴＞
・V0.0 2008/2/6	 プロトタイプ版
・V0.1 2008/2/8	 3in1/2in1のゲームに対応。
・V0.2 2008/2/10 SAVファイルの拡張子の大文字/小文字の区別を無くした(バグってゴメンなさい)。
		 BINファイルおよびUNKNOWNのゲームのSAVEサイズを64KBに変更。
		 NORモードのタイトルの色を変更。
		 PSRAMでの転送でDMAを使用するのを止めた(遅くなったけど安定した？)。
・V0.3 2008/2/21 R4/M3Sで、リセット無効に設定している時の不具合を修正。
		 EEPROM_V111のパッチ不具合の修正。
		 NORモードのFLASH1M_V103のパッチ不具合の修正。
		 「EZ4 lite-delux」と「EWIN EXPANSION PAK (2in1)」のサポート
		 PSRAM/SDRAMモードでのSAVEデータを、「GBA_ExpLoader」起動時にSAVファイルへ
		 書込むように仕様を変更(今までは次にRAMからGBA/BINを起動する時)。
・V0.4 2008/3/1  メッセージを少し修正。
		 EWIN EXP PAKで、拡張RAMやLINK等のリセット後に認識されないのを修正。
		 EWIN EXP PAKで、SRAMが256KB無い時の判定を修正。
		 SAVファイルを、SAVと<1>から<5>(sv1からsv5)の6種類から選択できるようにした。
・V0.5β 2008/3/9
		 Famicom Mini(Classic NES)のEEPROM_V124をサポート(EEPROM_V122は未サポート)。
		 EWIN EXPANSION PAK (2in1)のSRAMが、128KBのタイプを暫定ですがサポート。
		 GBAファイル時の自動ヘッダ修復機能を内蔵。
		 iniファイルにて、SAVE/SIGNのディレクトリとMultiSave機能の無効を指定できるようにした。
・V0.5β(1) 2008/3/10
		 モジュール不正により勝手に差換え

・V0.5 2008/3/12 これより正式版
		 Famicom Mini(Classic NES)のEEPROM_V122と未定義タイプをサポート。
		 「DS振動カートリッジ」に設定した後の初期化の不具合を修正。
		 ディレクトリの作成日付を入れるように修正。
		 GBAのファイル名が、ショートネーム(半角8文字以内+.GBA)の場合に正しくSAVファイルを
		 認識していなかった点を修正。
・V0.51 2008/3/15
		 エイリアス名を、Windows互換になるようにlibfatを修正(デジットは2桁に固定)。
		 よって、0xE5問題("薔薇も使えます.gba")と空白・日本語を使用したショート名に対応。
		 拡張カード判定を修正(変化ないかも？)。
		 [EXP128K]時のSRAM.BINの処理の不具合を修正
・V0.53 2008/3/22
		 SRAMが128Kの「DSTT GBA&EXPLORER 2IN1」での判定の不具合を修正。
		 「M3」「G6」「GBA Expansion Pack」の暫定サポート(FLASH1Mタイプのパッチは未実装)。
		 ソフトリセット不可時での表示の不具合を修正。
		 正しくSLOT-1タイプになっていない、SLOT-1のDLDIに対応。
・V0.54 2008/3/23
		 「M3」「G6」「GBA Expansion Pack」のSRAMの一部を壊わしてしまう不具合のため差換え。
・V0.55 2008/3/30
		 NOR書込み時の不具合を修正。
		 「DSTT GBA&EXPLORER 2IN1」時に、SAVE管理をファイルにすることによりFLASH1Mタイプをサポート。
・V0.56 2008/4/13
		 SAVEのタイムスタンプ値の不正を修正。
		 日本語ファイル名の表示時で、行末の処理を追加。
		 ショートネーム(半角8文字以内+.GBA)の場合に大文字/小文字混在時の不具合を修正。
・V0.57 2008/5/12
		 SAVEのタイムスタンプ値の不正を再度修正(おそらく今度は大丈夫？)。
		 Famicom Mini(Classic NES)のSAVEデータをVBAと同じに形式に変更。よって、今までのSAVEとは
		 互換性がなくなったので注意が必要です(すいません！)。

by Rudolph (皇帝)
