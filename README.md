# Activity扩展——PreferenceFragment

##### SettingActivity.java
```
public class SettingActivity extends PreferenceActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        //addPreferencesFromResource(R.xml.preferences);
        getFragmentManager().beginTransaction()
                .replace(android.R.id.content, new SettingsFragment())
                .commit();
    }

    public static class SettingsFragment extends PreferenceFragment {
        @Override
        public void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            addPreferencesFromResource(R.xml.preferences);
        }
    }
}
```


#### 1、CheckBoxPreference
```
 <PreferenceCategory
        android:title="@string/In_line_preferences"
        >
    <CheckBoxPreference
        android:key="key_CheckBoxPreference"
        android:summary="@string/CheckBoxPreference_summary"
        android:title="@string/CheckBoxPreference_title"
        android:text="11"
        android:defaultValue="false" />
    </PreferenceCategory>
```
![CheckBoxPreference](https://i.loli.net/2019/04/11/5caea33cd817c.jpg)

#### 2、Dialog-based preferences
##### ①EditTextPreference
```
 <EditTextPreference
            android:key="key_EditTextPreference"
            android:title="@string/EditTextPreference_title"
            android:summary="@string/EditTextPreference_summary"
            android:dialogTitle="@string/EditTextPreference_dialog_title"/>
```
![EditTextPreference](https://i.loli.net/2019/04/11/5caea33d25195.jpg)
![EditTextPreference](https://i.loli.net/2019/04/11/5caea33d0903a.jpg)

##### ②ListPreference
```
 <ListPreference
            android:key="key_ListPreference"
            android:title="@string/ListPreference_title"
            android:summary="@string/ListPreference_summary"
            android:dialogTitle="@string/ListPreference_dialog_title"
            android:entries="@array/choose_one"
            android:entryValues="@array/choose_one_values"/>
```
![ListPreference](https://i.loli.net/2019/04/11/5caea33d368b5.jpg)
![ListPreference](https://i.loli.net/2019/04/11/5caea33d16f0a.jpg)

#### 3、PreferenceScreen
##### ①PreferenceScreen: 跳转到另一个PreferenceScreen
```
 <PreferenceScreen
            android:key="key_Screen_preference"
            android:title="@string/Screen_preference_title"
            android:summary="@string/Screen_preference_summary">
            <CheckBoxPreference
                android:key="key_Screen_checkbox"
                android:title="@string/Screen_checkbox_title"
                android:summary="@string/Screen_checkbox_summary"/>
        </PreferenceScreen>
```
![跳转到另一个PreferenceScreen](https://i.loli.net/2019/04/11/5caea384add44.jpg)
![跳转到另一个PreferenceScreen](https://i.loli.net/2019/04/11/5caea38483de5.jpg)

##### ②启动一个网页
```
 <PreferenceScreen android:title="@string/Intent_preference_title"
            android:summary="@string/Intent_preference_summary">
            <intent android:action="android.intent.action.VIEW"
                android:data="http://www.baidu.com"/>
        </PreferenceScreen>
```

![ 启动一个网页](https://i.loli.net/2019/04/11/5caea384de068.jpg)
![ 启动一个网页](https://i.loli.net/2019/04/11/5caea384f0f75.jpg)

##### 3、Preference attributes
*CheckBox: 父选项
CheckBox: 子选项，当父选项勾选时呈现*
```
<PreferenceCategory
        android:title="@string/Preference_attributes">
        <CheckBoxPreference
            android:key="key_Parent_checkbox_preference"
            android:title="@string/Parent_checkbox_preference_title"
            android:summary="@string/Parent_checkbox_preference_summary"/>
        <CheckBoxPreference
            android:key="key_Child_checkbox_preference"
            android:title="@string/Child_checkbox_preference_title"
            android:summary="@string/Child_checkbox_preference_summary"
            android:dependency="key_Parent_checkbox_preference"/>
    </PreferenceCategory>
```
![](https://i.loli.net/2019/04/11/5caea3851b97b.jpg)
![](https://i.loli.net/2019/04/11/5caea7457a3ad.jpg)
