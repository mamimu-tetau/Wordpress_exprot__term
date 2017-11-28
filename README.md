## Wordpressのtermとかtaxonomyとかの出力関連

### Archive.phpなどでterm取得（1個だけ）
```
<?php $terms = get_the_terms( $post->ID, '$taxonmy' );
  if ($terms && ! is_wp_error($terms)): ?>
  <?php foreach($terms as $term): ?>
    <?php echo $term->name; break; ?>
  <?php endforeach; ?>
<?php endif; ?>
```

### sigle.phpとかで同じtermの記事表示させるとか（term ID取得1個だけ ）
<?php $terms = get_the_terms( $post->ID, '$taxonmy' );?>
//term取得

<?php
	if( $terms ) {
		foreach($terms as $term){
			echo '<a href="' . get_term_link( $term->slug, 'workscat') . '">' . $term->name . '</a>';
			break;
		}
	}
?>
//term取得

<?php
  $relation_terms = get_the_terms($post->ID, '$taxonmy' );
  $term_id = array();
  if( $relation_terms ) {
    foreach ( $relation_terms as $term ) {
      array_push( $term_id, $term->term_id );
      break ;
      }
    }
?>
