---
title: ImportParties 命令 |Microsoft Docs
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
ms.openlocfilehash: a6c25b913b6479b857fb7cee4aec10e6984f2195
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998535"
---
# <a name="importparties-command"></a>ImportParties 命令
企業對企業的合作對象和協議從檔案匯入來源 XML 繫結在組態資料庫中，但不匯入的任何應用程式成品。 如需詳細資訊，請參閱 <<c0>  **備註**本主題中。  

> [!IMPORTANT]
> 此命令的新開頭**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**，以及所有較新版本。
> 
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中產生的繫結檔案均未指定應用程式。 這些檔案將匯入到預設的應用程式。  
  
## <a name="usage"></a>使用方式  
  **BTSTask ImportParties-來源**:*值*[**-ExcludeEdiFallbackSettings**] [**-Server**:*值*] [**-資料庫**:*值*]
  
## <a name="parameters"></a>參數  
  
|參數|必要項|ReplTest1|  
|---|---|---|  
|**原始碼** | 必要項 | 要讀取之 XML 繫結檔案的路徑和檔案名稱。|
|**-ExcludeEdiFallbackSettings** | 選擇性 | 如果指定，將會排除 edi 後援 （x12 和 edifact） 設定繫結檔案。  |
| **伺服器** | 選擇性 | 裝載 BizTalk 組態資料庫的 SQL server 名稱。 |
| **-資料庫** | 選擇性 | BizTalk 組態資料庫的名稱。 |

## <a name="sample"></a>範例
  `BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

## <a name="remarks"></a>備註
如果繫結檔案中也有應用程式成品，然後它們不會匯入。 只有合作對象與合約匯入。