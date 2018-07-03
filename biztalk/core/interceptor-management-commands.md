---
title: 攔截器管理命令 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2be6460-1f81-4bc3-a831-34ff24d65d34
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aefeefc7010c4cefca323782dac5a1349479a07d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023164"
---
# <a name="interceptor-management-commands"></a>攔截器管理命令
為了支援新的 BAM 攔截器功能，BAM 管理公用程式中已加入四個新的命令。  
  
 這些命令支援攔截器的部署、擷取和移除。 也有提供一個命令給設定的攔截器清單。  
  
-   部署攔截器： 部署攔截器組態。  
  
-   取得 interceptorlist： 取得部署攔截的活動清單。  
  
-   取得攔截器： 取得攔截器組態。  
  
-   移除攔截器： 移除攔截器組態。  
  
> [!NOTE]
>  您可以藉由啟用任何 BM 公用程式命令的追蹤 **-追蹤： 在&#124;關閉**切換參數。 使用追蹤參數會覆寫組態檔中的追蹤設定。 此參數可以搭配任何一般 BM 命令使用。  
  
> [!NOTE]
>  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。  
  
## <a name="deploy-interceptor-command"></a>deploy-interceptor 命令  
 **Usage**  
  
 **bm.exe 部署攔截器檔案名稱：\<組態 XML 檔名\>[-Force: True] [-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|描述|  
|---------------|-----------------|  
|檔案名稱：\<組態 XML 檔案名稱\>|包含攔截器組態的 XML 檔案名稱。|  
|Force:True|選擇性： 偵測到事件來源名稱衝突時，會強制部署攔截器組態。|  
|伺服器：\<伺服器\>|選擇性： 要部署攔截器的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。|  
|資料庫：\<資料庫\>|選擇性： 要設定攔截器的 BAM 主要匯入資料庫的名稱。|  
  
 這個命令會將攔截器組態部署到指定的伺服器和資料庫。 在部署期間，BAM 管理公用程式會執行下列驗證：  
  
- XSD 驗證： 針對一般攔截器組態結構描述驗證的攔截器組態。  
  
- 此活動存在 (在主要匯入資料庫中部署) 且檢查點有效 (存在而且有相符的資料類型) 的驗證。  
  
  如果在事件來源名稱中偵測到衝突，會擲回一則警告來描述此衝突。 如果發生衝突，部署會失敗，除非 **– Force: True**使用參數的旗標。  
  
> [!NOTE]
>  **– Force: True**參數可能會移除參考具有相同名稱的事件來源的攔截器組態。 您應該使用**取得攔截器**命令來建立現有攔截器組態的備份，再使用 **– Force: True**參數。  
  
 **範例**  
  
```  
bm.exe deploy-interceptor  -FileName:myInceptor.xml  
bm.exe deploy-interceptor  -FileName:myInceptor.xml -Force:True  
```  
  
## <a name="get-interceptorlist-command"></a>get-interceptorlist 命令  
 **Usage**  
  
 **bm.exe get interceptorlist [-Server:\<伺服器\>] [-Database:\<資料庫\>]**  
  
 **參數**  
  
|參數|描述|  
|---------------|-----------------|  
|伺服器：\<伺服器\>|選擇性： 要從中傳回一份已部署攔截器的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。|  
|資料庫：\<資料庫\>|選擇性： 要從中擷取已部署攔截器的 BAM 主要匯入資料庫的名稱。|  
  
 這個命令會傳回已啟用攔截之活動和其相關事件來源的清單。  
  
 **範例**  
  
```  
bm.exe get-interceptorlist   
```  
  
## <a name="get-interceptor-command"></a>get-interceptor 命令  
 **Usage**  
  
 **bm.exe 取得攔截器 [-Server:\<伺服器\>] [-Database:\<資料庫\>]-FileName:\<組態 XML 檔案名稱\>[-活動：\<活動名稱\>][-EventSource:\<事件來源名稱\>]**  
  
 **參數**  
  
|參數|描述|  
|---------------|-----------------|  
|伺服器：\<伺服器\>|選擇性： 要從中擷取已部署之攔截器的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。|  
|資料庫：\<資料庫\>|選擇性： 要從中擷取已部署之攔截器的 BAM 主要匯入資料庫的名稱。|  
|檔案名稱：\<組態 XML 檔案名稱\>|寫入攔截器組態的目標 XML 檔案名稱。|  
|活動：\<活動名稱\>|選擇性︰ 指定要傳回設定之攔截器的活動。 可以用於搭配**EventSource**參數來進一步指定要傳回的組態。|  
|EventSource:\<事件來源名稱\>|選擇性︰ 指定要傳回設定之攔截器的事件來源。 可以用於搭配**活動**參數來進一步指定要傳回的組態。|  
  
 如果未提供任何活動名稱或事件來源名稱，此命令會傳回有效的組態檔，其中包含所有事件來源和活動的攔截器組態。  
  
 如果只有提供活動名稱，此命令會針對該活動的所有事件來源傳回有效的攔截器組態檔。  
  
 如果只有提供事件來源名稱，此命令會針對所有活動中的該事件來源傳回有效的攔截器組態檔。  
  
 如果活動名稱和事件來源名稱都有提供，此命令會針對該活動的該事件來源傳回有效的攔截器組態檔。  
  
 **範例**  
  
```  
bm.exe get-interceptor   
bm.exe get-interceptor  -Activity:ShippingPO  
```  
  
## <a name="remove-interceptor-command"></a>remove-interceptor 命令  
 **Usage**  
  
 **bm.exe 移除攔截器 [-Server:\<伺服器\>] [-Database:\<資料庫\>] [-活動：\<活動名稱\>] [-EventSource: \<的事件來源名稱\>]**  
  
 **參數**  
  
|參數|描述|  
|---------------|-----------------|  
|伺服器：\<伺服器\>|選擇性： 要設定攔截器所在的伺服器名稱。 伺服器和執行 bm.exe 的電腦必須位在相同網域中。|  
|資料庫：\<資料庫\>|選擇性： 要設定攔截器所在之資料庫的名稱。|  
|活動：\<活動名稱\>|選擇性︰ 指定要移除指定之攔截器的活動。 可以用於搭配**EventSource**參數來進一步指定要傳回的組態。|  
|EventSource:\<事件來源名稱\>|選擇性︰ 指定要移除指定之攔截器的事件來源。 可以用於搭配**活動**參數來進一步指定要傳回的組態。|  
  
 如果只有提供活動名稱，此命令會針對該活動的所有事件來源移除攔截器。  
  
 如果只有提供事件來源名稱，此命令只會移除所有活動的該事件來源部分。  
  
 **範例**  
  
```  
bm.exe remove-interceptor   
```  
  
## <a name="see-also"></a>另請參閱  
 [BAM 管理公用程式](../core/bam-management-utility.md)