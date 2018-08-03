---
title: 使用繫結檔案匯入或匯出 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9a2a82a-f8d4-4ec2-b8c1-be6cda3f993a
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9ed0f50d6a6d841169b16f3f3ffd485ee345aeb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990591"
---
# <a name="use-binding-files-to-import-or-export"></a>使用繫結檔案匯入或匯出

開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]，您可以匯出並匯入繫結檔案，在**合作對象**並**協議**層級。 針對先前的 BizTalk 版本，您匯出應用程式層級，就在所述： 

* [如何匯出 EDI-AS2 解決方案的繫結](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [如何匯入 EDI-AS2 解決方案的繫結](../core/how-to-import-bindings-for-an-edi-as2-solution.md)

本主題示範如何匯入和匯出合作對象、 其設定檔、 協議、 後援設定和更多使用[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]和 BTSTask。 

## <a name="overview"></a>概觀

匯入和匯出功能包括：

* 從 XML 繫結檔案匯入合作對象、 商務設定檔與協議
* 將合作對象、 商務設定檔、 協議和 EDI 後援設定匯出到 XML 繫結檔案
* 匯入繫結檔案時，您可以選擇匯入合作對象或後援設定
* 當匯入合作對象層級，只有合作對象和協議內繫結檔案匯入
* 將特定合作對象匯出至相同的繫結檔案，並選擇也會匯出這些合作對象相關聯的所有合約
* 應用程式匯入繫結精靈 可讓您選擇要匯入追蹤設定，或排除合作對象。
* 包含 BTSTask`ImportParties`和`ExportParties`命令 

## <a name="prerequisites"></a>必要條件

* 您必須以成員的帳戶登入 * * BizTalk Server 系統管理員 」 群組。 請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  

* 您必須新增的參考**BizTalk EDI 應用程式**從 BizTalk 應用程式將用於做為 EDI 應用程式。 請參閱[後續設定步驟](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)。

## <a name="import-or-export-all-the-trading-partners"></a>匯入或匯出所有交易夥伴
1. 開啟**[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，再展開 BizTalk 群組。
2. 以滑鼠右鍵按一下**合作對象**，然後選取**匯出**。 

    當您匯出動作目前**合作對象**-層級，您要匯出所有交易夥伴。 這也會匯出交易夥伴，包括商務設定檔與協議到 XML 檔案所使用的所有項目。 

3. 以滑鼠右鍵按一下**合作對象**，選取**匯入**，然後選取繫結 XML 檔案。 

      若要選擇**排除合作對象**，或**排除 EDI 後援設定**讓它們不會匯入。 否則，繫結檔案中的所有項目會匯入，包括交易夥伴、 商務設定檔與協議。     

### <a name="btstask-example"></a>BTSTask 範例

`BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

請參閱[ImportParties 命令](../core/importparties-command.md)。

    
## <a name="export-individual-partners"></a>匯出個別的合作夥伴
1. 在  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，選取**合作對象**。
2. 在 **合作對象與商務設定檔**窗格中，以滑鼠右鍵按一下合作對象，然後選取**匯出**。

    當您匯出特定合作對象時，您可以選擇要匯出所有的合作對象，並使用該合作對象的協議。 您可以取消勾選**匯出選取的合作對象與選取的合作對象中的所有合約**只匯出您所選取的合作對象。

3. 選取 [確定]。 

> [!TIP]
> 在**合作對象與商務設定檔**窗格中，您也可以使用**CTRL**並**Shift**清單中選取多個合作對象的索引鍵。 您選取的合作對象的所有匯出至相同的繫結檔案。

### <a name="btstask-example"></a>BTSTask 範例

`BTSTask ExportParties -Destination:"C:\Temp\MyParties.Xml"`

請參閱[ExportParties 命令](../core/exportparties-command.md)。


## <a name="import-application-binding-file"></a>匯入應用程式繫結檔案

在應用程式層級，您可以將繫結檔案匯入與 EDI 和 AS2 合作對象。 

1. 在  **[!INCLUDE[btsBizTalkServerAdminConsoleui_md](../includes/btsbiztalkserveradminconsoleui-md.md)]**，展開 **應用程式**
2. 以滑鼠右鍵按一下您的應用程式，然後選取**匯入**。
3. **匯入追蹤設定**並**排除合作對象**選項可用。 使用這些選項，您可以選擇要匯入任何現有的追蹤設定，或排除繫結檔案中的任何 EDI/AS2 合作對象。

    | 設定 | 詳細資料 |
    |---|---|
    |**匯入追蹤設定** | 匯入應用程式，例如追蹤訊息內文，以及追蹤事件內的不同成品上啟用的追蹤設定。 <br/><br/>依預設啟用，以確保回溯相容性。 |
    | **排除合作對象**|執行檔案中現有的未匯入合作對象、 設定檔與協議。 <br/><br/>為了確保回溯相容性的預設為停用。|

   > [!IMPORTANT]
   > 全域追蹤設定會覆寫**匯入追蹤設定**。 因此如果您已停用追蹤，在全域層級，任何追蹤設定不會匯入，即使**匯入追蹤設定**已核取。
   > 
   > **BizTalk 設定儀表板，群組頁面**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]說明**允許匯入追蹤設定**全域設定。

### <a name="btstask-example"></a>BTSTask 範例

`BTSTask ImportBindings -ApplicationName:MyApplication -Source:C:\Bindings\Binding1.xml -ImportTrackingSettings:true`

請參閱[ImportBindings 命令](../core/importbindings-command.md)。

## <a name="in-this-section"></a>本節內容
若要匯入或匯出舊版 BizTalk EDI 和 AS2 繫結檔案，請參閱： 

* [如何匯出 EDI-AS2 解決方案的繫結](../core/how-to-export-bindings-for-an-edi-as2-solution.md)
* [如何匯入 EDI-AS2 解決方案的繫結](../core/how-to-import-bindings-for-an-edi-as2-solution.md)
