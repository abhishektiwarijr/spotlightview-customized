# spotlightview-customized
It is made by editing and combing 2 libraries in order to add custom views, you can make your in app tutorials using this spotlightview.I bet you won't be disappointed.

# How to use

        public class CommonUtils {
        public static SpotLightViewBuilder getGuide(final Activity activity, final View targetView, final String                           subHeadingText,final String usageId, final String headerText) {
        SpotLightViewBuilder spotlightView = SpotLightViewBuilder.initialize(activity);
        spotlightView.setIntroAnimationDuration(400);
        spotlightView.setRevealAnimationEnabled(true);
        spotlightView.performClick(true);
        spotlightView.addCustomView(R.layout.layout_tut);
        spotlightView.fadeInTextDuration(400);
        spotlightView.subHeadingTvColor(Color.parseColor("#ffffff"));
        spotlightView.subHeadingTvSize(16);
        spotlightView.subHeadingTvText(subHeadingText);
        spotlightView.setMaskColor(Color.parseColor("#dc000000"));
        spotlightView.target(targetView);
        spotlightView.lineAnimDuration(400);
        spotlightView.lineAndArcColor(Color.parseColor("#ffffff"));
        spotlightView.setCustomViewHeaderText(R.id.tvHeaderTut, headerText);
        spotlightView.dismissOnTouch(false);
        spotlightView.dismissOnBackPress(true);
        spotlightView.enableDismissAfterShown(false);
        spotlightView.usageId(usageId); //UNIQUE ID
        spotlightView.show();
        return spotlightView;
                }
    ...
         }
   
   
   
   # Now,In your activity or fragment use like below or as you wish
   
    new Handler(Looper.getMainLooper()).postDelayed(new Runnable() {
            @Override
            public void run() {
                final SpotLightViewBuilder spotlightView = CommonUtils.getGuide(RFIDAndManualCheckingActivity.this, binding.ivRfidEntry, "You can check the details\nof the rider.", "rv1", getString(R.string.boarding));
                spotlightView.setClickListenerOnView(R.id.ivToolbarLeftTut, new View.OnClickListener() {
                    @Override
                    public void onClick(View v) {
                        //spotlightView.removeSpotlightView(false);
                
                    }
                });
            }
        }, 400);
        mPreferencesManager.resetAll();


# Note: Always make an instance of Preference manager and reset it always when used spotlightview,E.g:

        private PreferencesManager mPreferencesManager= new PreferencesManager(RFIDAndManualCheckingActivity.this);
        
        //After viewing spotlight
        
        mPreferencesManager.resetAll();
