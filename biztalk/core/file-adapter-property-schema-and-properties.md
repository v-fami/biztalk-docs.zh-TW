---
title: File 配接器屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], properties
- schemas, File adapters
- File adapters, schemas
- Password property [File adapters]
- ReceivedFileName property [File adapters]
- configuring [File adapters], schemas
- CopyMode property [File adapters]
- AllowCacheOnWrite property [File adapters]
- FileCreationTime property [File adapters]
- UserName property, File adapters
- File adapters, properties
- UserName property
ms.assetid: c5ae5339-67bf-4fde-a721-5b1aa3b9caca
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37e1c6860b002b41555337a0bf7e8cb931f2c2bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22245990"
---
# <a name="file-adapter-property-schema-and-properties"></a>File 配接器屬性結構描述和屬性
下表包含 FILE 配接器屬性結構描述中的屬性。  
  
 **命名空間：** http://schemas.microsoft.com/BizTalk/2003/file-properties  
  
|名稱|型別|Description|  
|----------|----------|-----------------|  
|**CopyMode**|xs:unsignedInt|定義將訊息寫入檔案時使用的複製模式。 有效值為：<br /><br /> **附加 (0)。** 若檔案存在，FILE 傳送處理常式會開啟檔案，並將訊息附加到檔案結尾。 若檔案不存在，FILE 傳送處理常式會建立新檔案。<br /><br /> **建立新的 (1)。** 若檔案不存在，FILE 傳送處理常式會建立新檔案並寫入檔案。 若檔案已存在，FILE 傳送處理常式會報告錯誤，然後依照傳送埠的一般配接器重試邏輯來處理。 此為 FILE 傳送處理常式的預設複製模式。<br /><br /> **覆寫 (2)。** 若檔案存在，FILE 傳送處理常式會開啟檔案，並覆寫其內容。 若檔案不存在，FILE 傳送處理常式會建立新檔案。|  
|**AllowCacheOnWrite**|xs:Boolean|定義將訊息寫入檔案時，FILE 配接器是否使用檔案系統快取。|  
|**ReceivedFileName**|xs:string|定義 FILE 配接器從中讀取訊息之檔案的完整名稱。|  
|**FileCreationTime**|xs:datetime|定義檔案寫入由 FILE 接收配接器監控之資料夾的時間。|  
|**使用者名稱**|xs:string|定義當指定替代認證來存取網路共用時所使用的帳戶使用者名稱。|  
|**密碼**|xs:string|定義當指定替代認證來存取網路共用時所使用的帳戶密碼。|  
  
## <a name="see-also"></a>另請參閱  
 [設定 File 配接器](../core/configure-the-file-adapter.md)