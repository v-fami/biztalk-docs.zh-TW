---
title: ImportParties 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 87d43e2c-401c-4450-ad9b-2528086b99e4
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15edad97134d3dbccc6f4b1af9395cb0bc01febd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257006"
---
# <a name="importparties-command"></a>ImportParties 命令
企業對企業合作對象和協議從檔案匯入來源 XML 繫結在組態資料庫中，而不匯入的任何應用程式成品。 如需詳細資訊，請參閱**備註**本主題中。  

> [!IMPORTANT]
> 這個命令是新開頭 **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，以及所有較新版本。
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中產生的繫結檔案均未指定應用程式。 這些檔案將匯入到預設的應用程式。  
  
## <a name="usage"></a>使用方式  
  **BTSTask ImportParties-來源**:*值*[**-ExcludeEdiFallbackSettings**] [**-伺服器**:*值*] [**-資料庫**:*值*]
  
## <a name="parameters"></a>參數  
  
|參數|Required|值|  
|---|---|---|  
|**原始碼** | Required | 要讀取的 XML 繫結檔案路徑和檔案名稱。|
|**-ExcludeEdiFallbackSettings** | 選擇性 | 如果指定，它會從繫結檔案中排除 edi 後援 （x12 和 edifact） 設定。  |
| **伺服器** | 選擇性 | 裝載 BizTalk 組態資料庫的 SQL server 名稱。 |
| **資料庫** | 選擇性 | BizTalk 組態資料庫的名稱。 |

## <a name="sample"></a>範例
  `BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

## <a name="remarks"></a>備註
如果繫結檔案也會有應用程式成品，然後不匯入。 只有合作對象和協議才會匯入。