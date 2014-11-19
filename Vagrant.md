vagrantとは
-------------
違う環境に移行可能な開発環境を簡単に構築・管理し、配布することができる開発環境ツール。
簡単にテスト環境を手に入れることができる。変更になっても簡単に開発環境を捨てることができ、またすぐに別の環境ができるためトライ&エラーを繰り返せる。
vagrantを使うと簡単に仮想環境を作ることができる
vagrant起動
-------------
[vagrantbox](http://www.vagrantbox.es)
vagrantbox からboxをインストールしてくる
boxインストール仕方
$vagrant box add 名前 vagrantboxのurl
次にVagrantfileを作る
$vagrant init 名前　※名前はbox追加した時のと一緒にする
次にvagrantfileを編集する
$vi Vagrantfile

VAGRANTFILE_API_VERSION = "2"
vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box = box名前
	config.vm.network :public_network,:ip=>"x.x.x.x",:netmask=>"x.x.x.x"
	if Vagrant.has_plugin?("vagrant-proxyconf")
		config.yum_proxy.http = "http://172.16.40.1:8888/"
		config.proxy.http = "http://172.16.40.1:8888/"
		config.proxy.https = "http://172.16.40.1:8888/"
		config.proxy.no_proxy = "http://172.16.40.1,.it-college.ac.jp"
	end
end

次にvagrant起動
$vagrant up

次にvagrantに入る
$vagrant ssh



