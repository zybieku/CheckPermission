# CheckPermission
##Android权限处理,针对不同的系统版本##
###把工具类下载复制到你的项目中即可###
>使用:
``` 
    //检查语音权限
private void checkRecordPermission() {
    //6.0以上的权限检查
        if (Build.VERSION.SDK_INT >= 23) {
            if (!CheckPermissionUtils.getInstance()
                    .checkPermission23(this, CheckPermissionUtils.RECORD_AUDIO)) {
                ActivityCompat.requestPermissions(this,
                        new String[]{CheckPermissionUtils.RECORD_AUDIO},
                        CheckPermissionUtils.RECORD_PERMISSION_CODE);
            } else {
               //这里进行你正常逻辑的代码
            }
        } else {
          //6.0以下的权限检查
            if (!CheckPermissionUtils.getInstance().CheckRecordPermission(this)) {
                CheckPermissionUtils.getInstance().showPermissionDialog(this,getString(R.string.audio_permission),getString(R.string.microphone));
            } else {
                String strRewardTotal = CoinUtils.getFormatStringAfterSubtract(mStrReward, Double.toString(mCouponAmount));
                mPresenter.postPublishChatPal(mSecondLngCode, mSexCode, String.valueOf(Double.parseDouble(strRewardTotal) < 0 ? 0 : strRewardTotal), mStrDuration,
                        mLevel, mStrVolunteer, mVolunteerOnly, mCouponId);
            }
        }
    }
    //6.0以上的权限检查回调
    @Override
    public void onRequestPermissionsResult(int requestCode, String permissions[],
                                           int[] grantResults) {
        switch (requestCode) {
            case  CheckPermissionUtils.RECORD_PERMISSION_CODE: {
                if (grantResults.length > 0
                        && grantResults[0] == PackageManager.PERMISSION_GRANTED) {
                 //这里执行权限允许之后的正常逻辑代码
                } else {
                //这里是弹框提示
                    CheckPermissionUtils.getInstance().showPermissionDialog23(this,getString(R.string.audio_permission),getString(R.string.microphone));
                }
                return;
            }
        }
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
    }
    ```
