---
title: "檔案配接器組態屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- File adapters, code sample
- receive locations, adapters
- File adapters, send ports
- File adapters, receive locations
- File adapters, properties
- send ports, adapters
ms.assetid: 53f4fd17-95b9-4861-b433-772b619e90c7
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c027d5ab993c2110dbcbd6d992859d0d1d4ac7d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="file-adapter-configuration-properties"></a>FILE 配接器組態屬性
下表列出您可為 FILE 配接器接收位置設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|RemoveReceivedFileRetryCount|VT_UI4|指定 FILE 配接器嘗試刪除已讀取並提交至 BizTalk Server 的檔案的次數。|有效值介於 0 到 100 之間。|預設值為 5。|  
|RemoveReceivedFileMaxInterval|VT_UI4|指定 FILE 配接器在嘗試刪除已讀取並提交至 BizTalk Server 的檔案之前所等待的初始間隔 (以毫秒為單位)。|有效值從 1 到 1000 之間。|預設值是 10。|  
|FileMask|VT_BSTR|指定檔案的遮罩。|無|預設值為 *.xml。|  
|BatchSizeInBytes|VT_UI4|指定一批檔案傳送到 BizTalk MessageBox 的最大位元組總數。|有效值從 1024年到 104857600。|預設值為 102400 時。|  
|PollingInterval|VT_UI4|指定 FILE 配接器輪詢指定的新檔案位置的間隔 (以毫秒為單位)。|有效值介於 1000年到 3600000。|設為 1 則停用輪詢。|  
|BatchSize|VT_UI4|指定以一個批次提交的訊息數量上限。|有效值從 1 到 256。|預設值為 20。|  
|FileNetFailRetryCount|VT_UI4|指定當網路共用上的接收位置暫時無法使用時，嘗試存取該接收位置的重試間隔時間 (以分為單位)。|有效值介於 0 到 4294967295。|預設值為 5。|  
|RemoveReceivedFileDelay|VT_UI4|指定 FILE 配接器在嘗試刪除已讀取並提交至 BizTalk Server 的檔案之前所等待的初始間隔 (以毫秒為單位)。|此間隔會在每次重試間隔之後加倍，並以指定的重試間隔值為其上限。<br /><br /> 有效值從 1 到 1000 之間。|預設值是 10。|  
|RenameReceivedFiles|VT_BOOL|指定拾取檔案進行處理之前是否重新命名檔案。|有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值是 0。|  
|FileNetFailRetryCount|VT_UI4|指定當網路共用上的接收位置暫時無法使用時，嘗試存取該接收位置的次數。|有效值介於 0 到 4294967295。|預設值為 5。|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<RemoveReceivedFileRetryCount vt="19">5</RemoveReceivedFileRetryCount>  
<RemoveReceivedFileMaxInterval vt="19">300000</RemoveReceivedFileMaxInterval>  
<FileMask vt="8">*.xml</FileMask>  
<BatchSizeInBytes vt="19">102400</BatchSizeInBytes>  
<PollingInterval vt="19">60000</PollingInterval>  
<BatchSize vt="19">20</BatchSize>  
<FileNetFailRetryInt vt="19">5</FileNetFailRetryInt>  
<RemoveReceivedFileDelay vt="19">10</RemoveReceivedFileDelay>  
<RenameReceivedFiles vt="11">0</RenameReceivedFiles>  
<FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
</CustomProps>  
```  
  
 下表列出可為 FILE 配接器傳送埠設定的組態屬性：  
  
|屬性名稱|類型|Description|限制|註解|  
|-------------------|----------|-----------------|------------------|--------------|  
|使用者名稱|VT_BSTR|指定 FILE 配接器的主控件執行個體沒有網路共用的必要權限時，所使用的替代認證。|無|指定的使用者名稱格式\<網域 > \username。|  
|UseTempFileOnWrite|VT_BOOL|指定在寫入目標資料夾時所使用的暫存檔。 一旦完成寫入檔案，檔案會重新命名為 Filename 屬性所指定的值。|只有在 CopyMode 屬性的值設定為 2 (建立新物件) 時，此屬性才能設定為 -1 (true)。<br /><br /> 有效值為：<br /><br /> --1 (true)<br />-0 (false)|預設值為 0 (false)。|  
|CopyMode|VT_UI4|定義將訊息寫入檔案時使用的複製模式。|有效值為：<br /><br /> -0 （附加）<br />-1 （覆寫）<br />-2 （建立新物件）|預設值為 2 (建立新物件)。|  
|FileName|VT_BSTR|指定檔案傳送處理常式寫入訊息的檔案名稱。|這個屬性上有關限制的詳細資訊，請參閱[檔案遮罩和檔案名稱屬性的限制](http://msdn.microsoft.com/library/d8f5afd0-a61f-4c9b-8a57-4792e3054769)。|預設值為 %MessageID%.xml。|  
|AllowCacheOnWrite|VT_BOOL|指定將訊息寫入檔案時是否使用檔案系統快取。|有效值為：<br /><br /> -0 （不使用快取）<br />--1 （使用快取）|預設值為 0 (不使用快取)。|  
|密碼|VT_NULL|指定 FILE 配接器的主控件執行個體沒有網路共用的必要權限時，與 Username 屬性搭配使用的密碼。|當匯出繫結檔案時，一定會將這個值設定為 Null。 將此繫結檔案匯入到目標 BizTalk Server 組態之前，必須手動將密碼填入此欄位。|無|  
  
 下列程式碼顯示您用來設定屬性的 XML 字串格式：  
  
```  
<CustomProps>  
<Username vt="8">Domainname\User</Username>  
<UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
<CopyMode vt="19">1</CopyMode>  
<FileName vt="8">%MessageID%.xml</FileName>  
<AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
<Password vt="1" />  
</CustomProps>  
```