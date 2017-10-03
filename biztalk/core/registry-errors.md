---
title: "登錄錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5bf2cd-f807-4083-8687-4416a2ee2908
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c84ec2a1082f431fef8e06357f14cc9b621c6a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="registry-errors"></a>登錄錯誤
診斷及解決 WCF 登錄錯誤的資訊。  

## <a name="failed-to-access-the-registry"></a>無法存取登錄
  
||錯誤詳細資料|  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法開啟 HKLM\\{0}。|  
  
### <a name="explanation"></a>說明  
 此錯誤表示無法存取登錄。  
  
### <a name="user-action"></a>使用者動作  
 請確定您具有讀取存取登錄。 若要存取登錄，請確定您有系統管理員權限或連絡電腦的系統管理員。
 
## <a name="failed-to-obtain-biztalk-install-path"></a>無法取得 BizTalk 安裝路徑
  
||錯誤詳細資料|  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|無法從 HKLM 取得 BizTalk 安裝路徑\\{0}\\{1}|  
  
## <a name="explanation"></a>說明  
 此錯誤表示無法存取登錄，以及索引鍵的值不正確。  
  
## <a name="user-action"></a>使用者動作  
 請確定您具有讀取存取登錄。 請確定機碼具有正確的值。 若要存取登錄，請確定您有系統管理員權限或連絡電腦的系統管理員。 