---
title: "ExportParties 命令 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b421c8ed-d505-48ba-9d1d-8519c9d51750
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca525872ccc1cd941673189c4ac176fc4631f22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exportparties-command"></a>ExportParties 命令
將所有的合作對象和協議匯出為 XML 繫結檔案。

> [!IMPORTANT]
> 這個命令是新開頭 **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，以及所有較新版本。

## <a name="usage"></a>使用方式
  **BTSTask ExportParties-目的地**:*值*[**-伺服器**:*值*] [**-資料庫**:*值*]
  
## <a name="parameters"></a>參數

|參數|Required|值|  
|---|---|---|  
| **目的端** | Required | 要寫入的 XML 繫結檔案的路徑和檔案名稱。 |
| **伺服器** | 選擇性 | 裝載 BizTalk 組態資料庫的 SQL server 名稱。 |
| **資料庫** | 選擇性 | BizTalk 組態資料庫的名稱。|

## <a name="sample"></a>範例
  `ExportParties  -Destination:"C:\Temp\MyParties.Xml"` 

## <a name="remarks"></a>備註
  匯出合作對象、 合約和 EDI 後援設定。 沒有應用程式的成品都會匯出。
