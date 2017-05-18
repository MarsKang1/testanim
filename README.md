# testanim
1.视图动画
1.1首先要说明的是布局动画的基本使用在下面我们用一个简单的例子做具体说明
        AlphaAnimation alpha=new AlphaAnimation(0,1);//透明度变化动画
        alpha.setDuration(2000);// 透明度动画
        RotateAnimation rotate=new RotateAnimation(0,360,RotateAnimation.RELATIVE_TO_SELF,0.5f,RotateAnimation.RELATIVE_TO_SELF,0.5f);// 旋转动画
        rotate.setDuration(2000);

        ScaleAnimation scale=new ScaleAnimation(1.5f,1f,1.5f,1f);//大小变化的动画  
        scale.setDuration(2000);

        TranslateAnimation translate = new TranslateAnimation(0, 160, 0, 240); // 位移动画
        translate.setDuration(2000);

        AnimationSet set=new AnimationSet(false);//是否共享插值器
        set.addAnimation(alpha);
        set.addAnimation(rotate);
        set.addAnimation(scale);
        set.addAnimation(translate);
        iv_main.startAnimation(set);
1.2也可以继承Animation类
       class DouAnim extends Animation {
        //interpolatedTime 表示当前动画进行的时间与动画总时间 从0逐渐增大到1
        //t 传递当前动画对象
        @Override
        protected void applyTransformation(float interpolatedTime, Transformation t) {
            t.getMatrix().setTranslate(
                    (float) Math.sin(interpolatedTime * 50) * 8,
                    (float) Math.sin(interpolatedTime * 50) * 8
            );// 50越大频率越高，8越小振幅越小
            super.applyTransformation(interpolatedTime, t);
        }
    }
如果对于matrix不太了解的话可以看看 http://www.cnblogs.com/qiengo/archive/2012/06/30/2570874.html#code 里面讲的十分透彻
2.属性动画















