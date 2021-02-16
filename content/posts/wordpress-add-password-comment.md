---
title: "워드프레스 password로 입력하는 댓글 만들기"
slug: "Wordpress Add Password Comment"
categories: ["wordpress"]
tags: ["wordpress", "php"]
date: 2021-02-16T17:49:02+09:00
draft: false
---

## wp-admin > 설정 > 토론 > '댓글 글쓴이는 이름과 이메일을 채워야만 합니다' 해제

{{< figure src="/images/wp-admin-comments-check.png" alt="관리자 토론 > 댓글 글쓴이는 이름과 이메일을 채워야만 합니다" >}}


## custom-comments.php 파일 생성 
```php
<?php
if ( post_password_required() ) {
	return;
}

$twenty_twenty_one_comment_count = get_comments_number();
?>

<div id="comments" class="comments-area default-max-width <?php echo get_option( 'show_avatars' ) ? 'show-avatars' : ''; ?>">
<?php 
	
	function custom_fields($fields) {
		 $req = get_option( 'require_name_email' );
		 $aria_req = ( $req ? " aria-required='true'" : '' );
		 $fields[ 'author' ] = '<p class="comment-form-author">'.
		   '<label for="author">' . "이름". '</label>'.( $req ? '<span class="required">*</span>' : "" ). '<input id="author" name="author" type="text" value="'. esc_attr( $commenter['comment_author'] ) .
		   '" size="10" placeholder="이름" tabindex="1"' . $aria_req . ' /></p>';
		$fields[ 'email' ] = '<p class="comment-form-email">'.
		   '<label for="email">' . __( 'Email' ) . '</label>'.
		   ( $req ? '<span class="required">*</span>' : '').
		   '<input id="email" name="email" type="text" value="'. esc_attr( $commenter['comment_author_email'] ) .
		   '" size="30"  tabindex="2" aria-required="false"/></p>';
		 $fields[ 'password' ] = '<p class="comment-form-password">'.
		   '<label for="password">' . __( 'Password' ) . '</label>'.
		   '<input id="password" name="password" type="password" value="'. esc_attr( $commenter['password'] ) .
		   '" size="30" placeholder="비밀번호"  tabindex="3" /></p>';
	   return $fields;
     }
     add_filter('comment_form_default_fields', 'custom_fields');
		function remove_website_field($fields) {
			unset($fields['url']);
			unset($fields['cookies']);
			unset($fields['email']);
			return $fields;
		}
		 
		add_filter('comment_form_default_fields', 'remove_website_field');
	?>
	<?php
	comment_form(
		array(
			'logged_in_as'       => null,
			'title_reply'        => '',
			'title_reply_before' => '<h2 id="reply-title" class="comment-reply-title">',
			'title_reply_after'  => '</h2>',
			'label_submit' => '글쓰기',
		)
	);
	?>
	<?php
	if ( have_comments() ) :
        global $post;
		?>
		<h2 class="comments-title">
			<?php if ( '1' === $twenty_twenty_one_comment_count ) : ?>
                <?php
                
                if ($post->post_type == 'column') {
                    printf(
                        /* translators: %s: comment count number. */
                        '댓글 ' . $twenty_twenty_one_comment_count
                    );
                } else if ($post->post_type == 'book') {
                    printf(
                        /* translators: %s: comment count number. */
                        '한줄리뷰 ' . $twenty_twenty_one_comment_count
                    );
                }
		?>
			<?php else : ?>
				<?php
                
                if ($post->post_type == 'column') {
                    printf(
                        /* translators: %s: comment count number. */
                        '댓글 ' . $twenty_twenty_one_comment_count
                    );
                } else if ($post->post_type == 'book') {
                    printf(
                        /* translators: %s: comment count number. */
                        '한줄리뷰 ' . $twenty_twenty_one_comment_count
                    );
                }
				
				?>
			<?php endif; ?>
		</h2><!-- .comments-title -->

		<ol class="comment-list">
			<?php
			wp_list_comments(
				array(
					'avatar_size' => 60,
					'style'       => 'ol',
					'short_ping'  => true,
                    'callback' => 'custom_comments',
				)
			);
			?>
		</ol><!-- .comment-list -->

		<?php
		the_comments_pagination(
			array(
				'before_page_number' => esc_html__( 'Page', '' ) . ' ',
				'mid_size'           => 0,
				'prev_text'          => sprintf(
					'%s <span class="nav-prev-text">%s</span>',
					is_rtl() ? '>' : '<',
					esc_html__( 'Older comments', 'twentytwentyone' )
				),
				'next_text'          => sprintf(
					'<span class="nav-next-text">%s</span> %s',
					esc_html__( 'Newer comments', '' ),
					is_rtl() ? '<' : '>'
				),
			)
		);
		?>

	<?php endif; ?>

    <script>
	  	jQuery(document).ready(function($){
              $(".comment-reply-link").text("답글");
              $(".update-comment").click(function(e){
                e.preventDefault();
                if($(this).parent().find(".comment-password").css("display") == "inline-block") {
                      if($(this).parent().find(".comment-password").val() != '') {
                        var $this_comment_id = $(this).attr('id');
                      $.ajax({
                        type: "post",
                        dataType: "json",
                        url: '/wp-admin/admin-ajax.php',
                        data: {
                            action : 'check_comment_password', // wp_ajax_*, wp_ajax_nopriv_*
                            'comment_id': $this_comment_id,
                            'password': $(this).parent().find(".comment-password").val(),
                             },
                        success: function(msg){
                            console.log(msg);
                            if(msg[0].result === 'ok') {
                                location.reload();
                            } else {
                                alert('비밀번호가 다릅니다.');
                            }
                        },
                        error: function (errorThrown) {
                            console.log(errorThrown);
                        }
                    });
                      } else {
                        alert('비밀번호를 입력해주세요.');
                      }
                      
                  } else {
                    $(this).parent().find(".comment-password").css("display", "inline-block");
                  }
              });
			  $(".delete-comment").click(function(e) {
                    e.preventDefault();
                  if($(this).parent().find(".comment-password").css("display") == "inline-block") {
                      if($(this).parent().find(".comment-password").val() != '') {
                        var $this_comment_id = $(this).attr('id');
                      $.ajax({
                        type: "post",
                        dataType: "json",
                        url: '/wp-admin/admin-ajax.php',
                        data: {
                            action : 'check_comment_password', // wp_ajax_*, wp_ajax_nopriv_*
                            'comment_id': $this_comment_id,
                            'password': $(this).parent().find(".comment-password").val(),
                             },
                        success: function(msg){
                            console.log(msg);
                            if(msg[0].result === 'ok') {
                                location.reload();
                            } else {
                                alert('비밀번호가 다릅니다.');
                            }
                        },
                        error: function (errorThrown) {
                            console.log(errorThrown);
                        }
                    });
                      } else {
                        alert('비밀번호를 입력해주세요.');
                      }
                      
                  } else {
                    $(this).parent().find(".comment-password").css("display", "inline-block");
                  }
				  
			  });
		  });
	  </script>
</div><!-- #comments -->

```

## single.php 댓글 설정

```php
<?php if ( comments_open() && ! post_password_required() ) { comments_template( '/custom-comments.php', true ); } ?>

```
