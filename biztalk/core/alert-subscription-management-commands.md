---
title: "警示訂閱管理命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd6ad27-6217-466a-b616-4b26fb31b0af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914d5cd9ac19e160c1f26df3f762f81fb89345d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="alert-subscription-management-commands"></a>警示訂閱管理命令
BAM 管理公用程式訂閱管理命令可讓您使用警示訂閱。  
  
-   取得訂用帳戶： 取得警示的訂閱者的清單。  
  
-   新增訂閱： 訂閱者加入警示。  
  
-   移除訂用帳戶： 從警示移除訂閱者。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤**-追蹤： 在 &#124; 關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。  
  
## <a name="get-subscription-command"></a>get-subscription 命令  
 **使用方式**  
  
 **bm.exe get 訂閱-檢視：\<檢視名稱 >-警示：\<警示名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視名稱 >|指定的警示所在檢視的名稱。|  
|警示：\<警示名稱 >|要取得其訂閱的警示名稱。|  
|伺服器：\<伺服器 >|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 列出指定之警示的所有訂閱者。  
  
 **範例**  
  
```  
bm.exe get-subscriptions -View:SalesManagerView -Alert:SalesTooLow  
bm.exe get-subscriptions -View:Shipments -Alert:SlowShipment -Server:Ship1  
```  
  
## <a name="add-subscription-command"></a>add-subscription 命令  
 **使用方式**  
  
 **bm.exe 加入訂閱的檢視：\<檢視名稱 >-警示：\<警示名稱 >-AccountName:\<帳戶名稱 >-類型: [檔案 &#124;電子郵件] [-電子郵件：\<電子郵件地址 >] [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視名稱 >|指定警示所在檢視的名稱。|  
|警示：\<警示名稱 >|要訂閱的警示名稱。|  
|AccountName:\<帳戶名稱 >|訂閱警示的帳戶，格式為「網域\使用者」。|  
|類型: [檔案 &#124;電子郵件]|警示的傳遞類型。 如果您指定電子郵件的傳遞類型，則必須在命令列上包含電子郵件參數。|  
|電子郵件：\<電子郵件地址 >|選擇性： 將會傳遞警示通知電子郵件地址。|  
|伺服器：\<伺服器 >|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 為指定的帳戶新增訂閱至只訂的警示。  
  
 **範例**  
  
```  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:File  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:Email -Email:useremail@domain.com  
```  
  
## <a name="remove-subscription-command"></a>remove-subscription 命令  
 **使用方式**  
  
 **bm.exe 移除訂用帳戶-檢視：\<檢視名稱 >-警示：\<警示名稱 >-AccountName:\<帳戶名稱 > [-Server:\<伺服器 >] [-Database:\<資料庫 >]**  
  
 **參數**  
  
|參數|Description|  
|---------------|-----------------|  
|檢視：\<檢視名稱 >|指定警示所在檢視的名稱。|  
|警示：\<警示名稱 >|警示的名稱。|  
|AccountName:\<帳戶名稱 >|要從警示移除的帳戶，格式為「網域\使用者」。|  
|伺服器：\<伺服器 >|選擇性： 檢視所在的伺服器的名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。 如果沒有指定伺服器名稱，bm.exe 會使用 localhost 的預設名稱。|  
|資料庫：\<資料庫 >|選擇性： 檢視所在的資料庫名稱。 如果沒有指定名稱，bm.exe 會使用預設的名稱 BamPrimaryImport。|  
  
 從指定的警示移除指定之帳戶的訂閱。 指定之帳戶的所有訂閱都將移除。  
  
 **範例**  
  
```  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:domain\user  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:user -Server:s1  
```  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)