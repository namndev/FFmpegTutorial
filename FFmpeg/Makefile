clean:
	@rm -rf ./build/*

fetch_small_bunny_video:
	./fetch_bbb_video.sh

make_hello: clean
	docker run -w /files --rm -it  -v `pwd`:/files leandromoreira/ffmpeg-devel \
	  gcc -L/opt/ffmpeg/lib -I/opt/ffmpeg/include/ /files/0_hello_world.c \
	  -lavcodec -lavformat -lavfilter -lavdevice -lswresample -lswscale -lavutil \
	  -o /files/build/hello

run_hello: make_hello
	docker run -w /files --rm -it -v `pwd`:/files leandromoreira/ffmpeg-devel /files/build/hello /files/small_bunny_1080p_60fps.mp4

make_remuxing: clean
	docker run -w /files --rm -it  -v `pwd`:/files leandromoreira/ffmpeg-devel \
	  gcc -L/opt/ffmpeg/lib -I/opt/ffmpeg/include/ /files/2_remuxing.c \
	  -lavcodec -lavformat -lavfilter -lavdevice -lswresample -lswscale -lavutil \
	  -o /files/build/remuxing

run_remuxing_ts: make_remuxing
	docker run -w /files --rm -it -v `pwd`:/files leandromoreira/ffmpeg-devel /files/build/remuxing /files/small_bunny_1080p_60fps.mp4 /files/remuxed_small_bunny_1080p_60fps.ts

run_remuxing_fragmented_mp4: make_remuxing
	docker run -w /files --rm -it -v `pwd`:/files leandromoreira/ffmpeg-devel /files/build/remuxing /files/small_bunny_1080p_60fps.mp4 /files/fragmented_small_bunny_1080p_60fps.mp4 fragmented
