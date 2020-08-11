# AlivcVideoPlayView

I am going to write some sample.

AlivcVideoListView
1. RecyclerViewEmptySupport
1. BaseVideoListAdapter
1. PagerLayoutManager
1. AliListPlayer
1. TextureView
1. OnRefreshDataListener
```java
 mListPlayer.setOnRenderingStartListener(new IPlayer.OnRenderingStartListener() {
            @Override
            public void onRenderingStart() {
                // 2018/11/21 hidden cover
                BaseVideoListAdapter.BaseHolder holder = (BaseVideoListAdapter.BaseHolder) recycler.findViewHolderForLayoutPosition(mCurrentPosition);
                if (holder != null) {
                    holder.getCoverView().setVisibility(GONE);
                }
                if (mLoadingListener != null) {
                    mLoadingListener.onLoadingEnd();
                }
            }
        });
```
