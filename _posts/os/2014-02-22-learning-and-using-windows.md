---
layout: post
category: ����ϵͳ
title: Windows ѧϰ��ʹ��
tags : [Windows,����ϵͳ]
image:
    feature: feature.jpg
comments: true
share: true
---

## 1. ����

## 2. ���ÿ�

ʹ�á�mlink����������Ŀ¼���ܿ�ϵͳ�̡�

```bat
mlink /j link_dir original_dir
```

## 3. �����ļ�����

ͨ���ļ��ġ��������ԡ��͡��Զ������ԡ��С��ָ�Ĭ��ͼ�ꡱ������ϵͳ�����ļ���

## 4. �Զ�������

### 4.1. ���� `Consolas` ���ӵ���������

������� `Consolas` �����������ӵ���΢��ڣ�����������Ա⣬�༭ע���

```registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontLink\SystemLink]
```

�½�һ�� �����ַ���ֵ������Ϊ ��Consolas�������п�ѡ��

```
MSYH.TTC,Microsoft YaHei,112,110 //�ֺţ�9��10��11��14
MSYH.TTC,Microsoft YaHei,120,100 //�ֺţ�10��12
MSYH.TTC,Microsoft YaHei,128,96  //�ֺţ�9��11
MSYH.TTC,Microsoft YaHei
SIMYOU.TTF,YouYuan
SIMSUN.TTC,NSimSun
```

�½�һ�� �����ַ���ֵ������Ϊ ��Consolas Bold�������п�ѡ��

```
MSYHBD.TTC,Microsoft YaHei Bold,112,110 //�ֺţ�9��10��11��14
MSYHBD.TTC,Microsoft YaHei Bold,120,100 //�ֺţ�10��12
MSYHBD.TTC,Microsoft YaHei Bold,128,96  //�ֺţ�9��11
MSYHBD.TTC,Microsoft YaHei Bold
SIMYOU.TTF,YouYuan
SIMSUN.TTC,NSimSun
```

�Ƽ�������������������

```
Comic Sans MS = MSYH.TTF,128,96
Trebuchet MS = MSYH.TTF
Consolas = SIMYOU.TTF       //��΢��
Lucida Console = SIMYOU.ttf //�Ա�
Verdana = SIMYOU.TTF
Monaco = SIMYOU.TTF         //��խ
```

## 5. �޸� Windows 7 ����̨��CMD��������

### 5.1. ���ע���ϵͳ����ڵġ�TrueType������

```registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\fonts]
```

### 5.2. ��ע�������

```registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\WindowsNT\CurrentVersion\Console\TrueTypeFont]
```

### 5.3. ����������Ϊ��0936���Ŀ���̨���������Ĵ���ҳ�����壬ֵΪϵͳ����ڵġ�TrueType���������ơ�Ҳ��������������Ϊ��000���Ŀ���̨����������ҳ������

### 5.4. �޸Ŀ���̨��CMD��Ĭ��ֵ������

#### 5.4.1 ��ʽһ���޸�ע���

```registry
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Console\%SystemRoot%_system32_cmd.exe]
"FaceName"="��������"
```

#### 5.4.2 ��ʽ�������ӿ���̨��CMD����ݼ����޸Ŀ�ݼ����Լ�Ĭ��ֵ���������ƺʹ�С

### 5.5. ����������ɿ���̨��������޸�

## 6. ͨ������ע����ʹ�Ҽ��˵��򿪿���̨��CMD���ڵ�ǰĿ¼

```registry
Windows Registry Editor Version 5.00

[HKEY_CLASSES_ROOT\Directory\shell\opencmd]
@="���� CMD"
[HKEY_CLASSES_ROOT\Directory\shell\opencmd\command]
@="cmd.exe /k cd %1"
```

