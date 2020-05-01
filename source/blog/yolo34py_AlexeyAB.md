# yolo34py + AlexeyAB的坑
yolo原作者pjreddie不再更新了，yolo v4 是AlexeyAB的fork出品。  
曾經用yolo34py API+ official libdarknet.so，但把darknet轉成AlexeyAB版本後會出錯，貌似用AlexeyAB的darknet.py也會出錯。  
原因是free_network 的API不同。  
解決辨法可以參考https://github.com/AlexeyAB/darknet/issues/3467  
2 approachs:
1. modify free_network, compile new so -> the darknet binary might be broken
[我改了原用的free_network成_free_network, 然後加free_network給yolo34py用](https://github.com/htleeab/darknet/tree/compatible_free_network_interface)
1. add api_free_network and change API(darknet.py or yolo34py) -> not compatible with pjreddie

object/pointer construction也跟official不同，比較難兼容...今後如果要用yolov4，大概直接拋棄pjreddie和yolo34py了
